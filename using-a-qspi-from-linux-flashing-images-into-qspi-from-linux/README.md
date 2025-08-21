# Using a QSPI from Linux; flashing images into QSPI from Linux

This post shows how you can use a QSPI device from Linux:

-   Partition it
    
-   Erase it
    
-   Write data into it
    
    -   Such as BOOT.BIN files for Xilinx FPGA SoCs, or any other arbitrary data
    
-   Read from it
    

You'll need to have mtd-utils installed in your Linux system.

## Partitioning the QSPI

First, make sure your device tree contains an entry for the flash and specifies the partition layout with which you want Linux to view the QSPI. You can use a single partition for the entire QPSI and then manually write to offsets within the QSPI. Alternatively, you can split the QSPI into partitions and then write to the individual partitions from Linux.

You can use the \`mtdpart\` command to modify the partition layout after the system boots into Linux.

The partition scheme is just a way to impose a different view on the QSPI from within Linux. Fundamentally the QSPI is still just a big chunk of flash. However, partitions provide some advantages:

-   The partitions specify the logical regions of the QSPI, with their locations and sizes. This removes the need to manually calculate the absolute offsets for where you want to place data. This also serves as a (weak) form of documentation.
    
-   Linux won't let you write past the end of a partition (into the next logical region of flash), so you don't accidentally mangle other things in the flash when you try to write a file that is too big to fit into its partition.
    

As an example, suppose your QPSI is 128 MiB (1 gigabit) large, and your microcontroller expects:

-   the bootloader to be placed at the base of the QSPI flash (offset 0)
    
-   a secondary backup bootloader to exist at a 512 KiB offset from the beginning of the QSPI
    
-   the region from 1 MiB to 6 MiB to be reserved for it for its own use
    
-   and you're using the remainder of the QSPI for arbitrary data that you want to store
    

Here's a sample device tree entry that specifies the partition layout from that example:

-   The first partition starts at the base of the QSPI (offset 0) and has a size of 512 KiB (0x80000 bytes) to fill up all the space to the beginning of the second partition.
    
-   The second partition starts at 512 KiB (offset 0x80000, immediately after the first partition ends) and also has a size of 512 KiB (0x80000 bytes).
    
-   The third partition ranges from 1 MiB (offset 0x100000) to 6 MiB, so its size is 5 MiB (0x5000000).
    
-   The fourth partition starts at 6 MiB (0x600000) from the beginning of the QSPI and fills up the remaining 122 MiB = 0x7A00000 bytes available on your flash chip.
    

```
flash@0 {

	... /* QSPI device properties */

	partition@0 {
		label = "bootloader_primary";
		reg = <0x0 0x80000>;
	};
	partition@1 {
		label = "bootloader_secondary";
		reg = <0x80000 0x80000>;
	};
	partition@2 {
		label = "microcontroller_reserved";
		reg = <0x100000 0x500000>;
	};
	partition@3 {
		label = "qspi_data";
		reg = <0x600000 0x7A00000>;
	};
};
```

With this partition scheme specified, when you want to update the backup bootloader, you can flash it directly into the base (offset 0) of partition 1, and don't need to calculate the absolute offset that it needs to be at (which would be 512 KiB).

Or if you want the QSPI to have just one big 128 MiB (0x8000000 bytes) partition:

```
flash@0 {

	... /* QSPI device properties */

	partition@0 {
		label = "qspi";
		reg = <0x0 0x8000000>;
	};
};
```

In this case, you'll manually need to calculate the correct offset of every item you want to put into QSPI.

## Erasing the QSPI

First, find your mtd device. Linux places them at /dev/mtd\*. Pay attention to the "Name:" that mtdinfo prints, which corresponds to the "label" property from the device tree.

```
$ mtdinfo /dev/mtd1
mtd1
Name:                           bootloader_secondary
Type:                           nor
Eraseblock size:                65536 bytes, 64.0 KiB
Amount of eraseblocks:          8 (524288 bytes, 0.5 MiB)
Minimum input/output unit size: 1 byte
Sub-page size:                  1 byte
Character device major/minor:   90:4
Bad blocks are allowed:         false
Device is writable:             true
```

Then, erase the area you want to write. The number of bytes you specify must be a multiple of the eraseblock size. You can erase the whole partition or a portion of it.

To erase the entire 512 KiB partition:

Erase 512 KiB (524,288 bytes) from offset 0 within this partition

```
$ mtd_debug erase /dev/mtd1 0 524288
=> Erased 524288 bytes from address 0x00000000 in flash
```

To erase only the first 128 KiB (2 eraseblocks):

Erase 128 KiB (131,072 bytes = 0x20000 bytes) from offset 0 within this partition

```
$ mtd_debug erase /dev/mtd1 0 0x2000
=> Erased 131072 bytes from address 0x00000000 in flash
```

To erase the final 128 KiB of this partition:

Skip 384 KiB == 6 blocks == 393,216 bytes == 0x60000 offset

Then erase 128 KiB = 2 blocks = 131,072 bytes = 0x20000 bytes

```
$ mtd_debug erase /dev/mtd1 0x60000 0x20000
=> Erased 131072 bytes from address 0x60000 in flash
```

If you want to erase the entire QSPI, you'll need to erase each partition individually. If there's a gap between your partitions, you'll need to repartition the QSPI to be able to erase that section from Linux.

## Write new data into the QSPI

On this example machine, we need to place the secondary bootloader at a 512 KiB offset in the QSPI. That's where our second partition begins, so we can write it directly to the base (offset 0) of that partition. Alternatively, if the entire QSPI is configured as one partition, we'll need to specify that the data needs to be written to a 512 KiB offset within the partition.

The format of the write command is:

```
mtd_debug write <device> <offset> <len> <file>
```

So to write our data to the QSPI:

```
$ ls -l BOOT.BIN
=> BOOT.BIN is 172037 bytes

# If partitions have been set up, place at beginning of 2nd partition
$ mtd_debug write /dev/mtd1 0 172037 BOOT.BIN
=> Copied 172037 bytes from BOOT.BIN to address 0x00000000 in flash

# With a single QSPI partition, place at offset 512 KiB = 0x80000
$ mtd_debug write /dev/mtd0 0x80000 172037 BOOT.BIN

# wc provides a shortcut. Note:
$ wc -c BOOT.BIN
172037 BOOT.BIN

# So you can don't need to explicitly calculate and specify the size
# Instead, do:
$ mtd_debug write /dev/mtd1 0 $(wc -c BOOT.BIN)
$ mtd_debug write /dev/mtd0 0x80000 $(wc -c BOOT.BIN)
```

## Read data from the QSPI (verify write or erase)

The read command follows the same format as the write command:

```
mtd_debug read <device> <offset> <len> <file>
```

With a single partition:

```
# with the full partition layout specified
$ mtd_debug read /dev/mtd1 0 172037 readback
# with a single partition
$ mtd_debug read /dev/mtd0 0x80000 172037 readback

$ md5sum BOOT.BIN readback
=> they match
```

Like any other storage device, you can also read the QSPI partitions as a file.

```
$ hexdump -Cv /dev/mtd1 | head
=> the bootloader image header is visible and looks correct

# or with a single partition, have hexdump skip 512k
$ hexdump -Cv -s 0x80000 /dev/mtd0 | head
```

You can also use hexdump to check that the flash was erased properly; all bits should be high (0xff) after an erase.