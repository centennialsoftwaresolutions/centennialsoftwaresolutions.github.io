# Creating device tree overlays

This post provides an example of how you can create a device tree overlay .dtbo file. Once you've created the dtbo file, read [<u><span>"Using device tree overlays with Linux/Petalinux"</span></u>](https://www.centennialsoftwaresolutions.com/post/using-device-tree-overlays-with-petalinux) to apply the overlay.

## Overlay structure

On your system, you might have an EEPROM connected to channel 3 of an I2C mux connected to the Cadence I2C controller in the PS. If this EEPROM were on the same PCB as the FPGA (permanently connected), the final device tree source file which Petalinux would assemble during the build process would have a structure that would look something like this:

```
/ {                               // root node of the device tree
    amba {                        // FPGA PS
        i2c@ff010000 {            // I2C bus from Cadence I2C controller
            i2c-mux@70 {          // mux @ addr 0x70 on bus
                i2c@0 { ... };
                i2c@1 { ... };
                i2c@2 { ... };
                eeprom_i2c_bus: i2c@3 { // I2C bus on chan. 3 of mux
                    #address-cells = <1>;
                    #size-cells = <0>;
                    reg = <3>;
                    eeprom@50 {   // EEPROM on chan. 3 I2C bus
                        reg = <0x50>;
                        compatible = "atmel,24c128";
                    };
                };
                i2c@4 { ... };
                // ..., more channels
            };
        };
    };
};
```

However, suppose that the EEPROM was not permanently attached to the system but could instead be connected to and disconnected from the FPGA. If the EEPROM was not connected at system boot, then:

\- Linux would parse the device tree at boot

\- Linux would request that any drivers for the "atmel,24c128" compatible string (in this case, just the at24 driver) probe for the device at address 0x50 on this I2C bus

\- The driver would not successfully probe the device since it's not connected - or there might be another device connected at 0x50 instead of the EEPROM, in which case the probe should also fail

\- Thus, the at24 driver will never be fully initialized and bound to the device

\- If the EEPROM is plugged in later, nothing will happen because I2C does not provide a mechanism for a newly connected device to announce itself. As far as the kernel is concerned, the EEPROM never has and never will exist.

To solve this problem, you can place the device tree entry for the EEPROM in an overlay. Then, load the overlay after the EEPROM is plugged in, and Linux will try to initialize the driver and set up the device at that time. And if another device at 0x50 is plugged into the mux channel, you can unload the EEPROM's overlay and load the overlay of the other device.

In the device tree source snippet above, the red highlighted section is specific to the EEPROM. Everything except the red section is permanently connected to the FPGA; the overlay only needs to load and unload the red part. This red part, combined with information about its location/target, is called the 'fragment' in the overlay.

In addition to the device tree nodes to load, the overlay source file also needs to contain information on where the overlay is loaded (which node will the red section be a child of when loaded?). There are two separate ways to do this:

\- With a 'target-path' property: in this case, it would be "/amba/i2c@ff010000/i2c-mux@70/i2c@3".

\- With a 'target' (target label) property: The fragment needs to be inserted into the i2c@3 node when loaded. This node has a label in the device tree source: "eeprom\_i2c\_bus" (highlighted in teal in the device tree source above). Thus, the target could be specified as: <&eeprom\_i2c\_bus>.

## Creating the overlay

The overlay source file, let's call it eeprom.dts, would have contents:

```
/dts-v1/;
/plugin/;
/ {
    fragment@0 {
        /* only include one of the target lines, not both */
        target = <&eeprom_i2c_bus>;
        target-path = "/amba/i2c@ff010000/i2c-mux@70/i2c@3";
        __overlay__ {
            eeprom@50 {
                reg = <0x50>;
                compatible = "atmel,24c128";
            };
        };
    };
};
```

The \_\_overlay\_\_ node contains the thing to insert into the device tree (the red part), and the target or target-path property specifies where to insert this into the device tree.

An overlay can contain multiple fragments. For example, suppose that your hardware design uses a single connector to physically connect both the EEPROM and also a temperature sensor. If these devices were independently connectable, you would want each one of them to have its own overlay. But because they're both connected simultaneously as one unit, there logically should be a single overlay containing both of them. If the EEPROM and temperature sensor were both connected to channel 3 of the mux, they would have the same target node, so the \_\_overlay\_\_ part would contain entries for the EEPROM and temperature sensor. However, if the EEPROM was connected to channel 3 and the temperature sensor was connected to channel 4, the two devices would have different parent nodes; therefore, the overlay would need to contain multiple fragments.

Configuration 1: EEPROM and temperature sensor on same I2C bus

```
/dts-v1/;
/plugin/;
/ {
    fragment@0 {
        target-path = "/amba/i2c@ff010000/i2c-mux@70/i2c@3";
        __overlay__ {
            eeprom@50 {
                reg = <0x50>;
                compatible = "atmel,24c128";
            };
            tmp401@7a {
                reg = <0x7a>;
                compatible = "ti,tmp401";
            };
        };
    };
};
```

Configuration 2: on different I2C buses

```
/dts-v1/;
/plugin/;
/ {
    fragment@0 {
        target-path = "/amba/i2c@ff010000/i2c-mux@70/i2c@3";
        __overlay__ {
            eeprom@50 {
                reg = <0x50>;
                compatible = "atmel,24c128";
            };
        };
    };
    fragment@1 {
        target-path = "/amba/i2c@ff010000/i2c-mux@70/i2c@4";
        __overlay__ {
            tmp401@7a {
                reg = <0x7a>;
                compatible = "ti,tmp401";
            };
        };
    };
};
```

Once the .dts file is created, it can be compiled into a .dtbo file using the device tree compiler:

```
$ dtc -b 0 -@ -O dtb eeprom.dts -o eeprom.dtbo
```

This will generate the file 'eeprom.dtbo'

## Thoughts on target path vs. label

Using target labels is better from a design, cleanliness, and portability perspective compared to using target-path. If the physical hardware structure changes (e.g., new PCB revision) or the PL structure changes (for devices connected to the PL), the base system device tree will need to change to reflect this, and so the target path may also change. Therefore, the overlay would also need to be changed, recompiled, and redistributed to any systems using the old dtbo file. However, the changed base device tree will still have the eeprom\_i2c\_bus label in the right place, so if the overlay source file was using target labels then the overlay would not need to change.

This also means that a single overlay file which specifies a target label can be used across different hardware revisions. You may be using two FPGA designs on two PCBs in production. The first may have the mux connected to a soft I2C controller in the PL, and the EEPROM on channel 3 of the mux; and the second board may have a different PL design resulting in the I2C controller having a different address, with the EEPROM on channel 5 of the mux. The target paths would differ like so:

```
"/amba_pl@0/i2c@ff040000/i2c-mux@70/i2c@3"
```

```
"/amba_pl@0/i2c@ff030000/i2c-mux@70/i2c@5"
```

The overlay files for these two configurations would need to differ if using target-path. You would need to keep two .dts (overlay source) files in your repositories and would need to compile the two individual overlays and distribute the right version to each board. With target labels, a single overlay would work on both boards as long as both base device trees had the eeprom\_i2c\_bus label attached to the right node.