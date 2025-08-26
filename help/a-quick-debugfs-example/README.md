# A Quick debugfs Example

![tux_logo](tux_logo.png)

This posts shows how to create, build and run a quick debugfs tree on QEMU.

**Prerequisites**

If you want to build and run the code go through [Build the Linux kernel and Busybox and run them on QEMU](http://www.zachpfeffer.com/single-post/Build-the-Linux-kernel-and-Busybox-and-run-on-QEMU)

**The Code**

```
#include <linux/module.h>
#include <linux/debugfs.h>
#include <linux/kernel.h>

#define DEVS 30
#define REGS 32

u16 regs[DEVS][REGS];

static int find_addr_and_reg(void *data, int *addr, int *reg)
{
	int i, j;

	for (i = 0; i < DEVS; i++) {
		for (j = 0; j < REGS; j++) {
			if ((u16 *) data == ®s[i][j]) {
				*addr = i;
				*reg = j;
				return 0;
			}
		}
	}
	/* something went wrong, should never get here */
	return -1;
}

static int debugfs_u16_set(void *data, u64 val)
{
	int ret, addr, reg;

	ret = find_addr_and_reg((u16 *)data, &addr, ®);
	if (ret == 0)
		printk(KERN_INFO "addr = %d, reg = %d\n", addr, reg);
	else
		printk(KERN_INFO "0x%p not found\n", (u16 *)data);

	*(u16 *)data = val;
	return 0;
}
static int debugfs_u16_get(void *data, u64 *val)
{
	int ret, addr, reg;

	ret = find_addr_and_reg((u16 *)data, &addr, ®);
	if (ret == 0)
		printk(KERN_INFO "addr = %d, reg = %d\n", addr, reg);
	else
		printk(KERN_INFO "0x%p not found\n", (u16 *)data);

	*val = *(u16 *)data;
	return 0;
}
DEFINE_SIMPLE_ATTRIBUTE(fops_u16, debugfs_u16_get, debugfs_u16_set, "%llu\n");

int init(void)
{
	struct dentry *d, *s, *n;
	char dev_addr[8];
	char reg_addr[8];
	u8 i, j;

	d = debugfs_create_dir("ds", NULL);
	if (!d)
		return -ENOMEM;

	for (i = 0; i < DEVS; i++) {
		snprintf(dev_addr, sizeof(dev_addr), "%i", i);
		s = debugfs_create_dir(dev_addr, d);
		if (!s)
			return -ENOMEM;

		for (j = 0; j < REGS; j++) {
			snprintf(reg_addr, sizeof(reg_addr), "%i", j);
			n = debugfs_create_file(reg_addr, 0644, s, ®s[i][j],
						&fops_u16);
			if (!n)
				return -ENOMEM;
		}
	}
	return 0;
}
module_init(init);
```

**Build It**

1\. Set up a few variables

```
STAGE=$HOME/tl
TOP=$STAGE/teeny-linux
K=$STAGE/linux-4.10.6
```

2\. Save the code to a file called

```
$K/drivers/dump-regs.c
```

3\. Edit this file

```
vi $K/drivers/Makefle
```

4\. Add this line at the top

```
obj-y += dump-regs.o
```

5\. Build the kernel

```
cd $K
make O=$TOP/obj/linux-x86-allnoconfig
```

If you see something like:

```
 LD      arch/x86/boot/setup.elf
  OBJCOPY arch/x86/boot/setup.bin
  OBJCOPY arch/x86/boot/vmlinux.bin
  BUILD   arch/x86/boot/bzImage
Setup is 15772 bytes (padded to 15872 bytes).
System is 929 kB
CRC 6f8420cf
Kernel: arch/x86/boot/bzImage is ready  (#29)
make[1]: Leaving directory '/home/pfefferz/tl/teeny-linux/obj/linux-x86-allnoconfig'
```

Things are likely working.

**Run It**

1\. Open a new terminal

```
STAGE=$HOME/tl
TOP=$STAGE/teeny-linux
qemu-system-x86_64 \
    -kernel $TOP/obj/linux-x86-allnoconfig/arch/x86/boot/bzImage \
    -initrd $TOP/obj/initramfs.igz \
    -nographic -append "earlyprintk=serial,ttyS0 console=ttyS0"
```

2\. Run

If you see something like (you may need to hit Enter to get the prompt):

```
Freeing unused kernel memory: 452K
Write protecting the kernel read-only data: 4096k
Freeing unused kernel memory: 776K
Freeing unused kernel memory: 1764K

Boot took 0.80 seconds

/bin/sh: can't access tty; job control turned off
/ # input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input2
random: fast init done

/ # 
```

Things are likely working.

**Test It**

1\. On the terminal in QEMU run

```
for i in `seq 0 29`;
do
    for j in `seq 0 31`;
    do
        echo 0x1234 > /sys/kernel/debug/ds/$i/$j
    done
done  

for i in `seq 0 29`;
do
    for j in `seq 0 31`;
    do
        cat /sys/kernel/debug/ds/$i/$j
    done
done 
```

If you see lots of output like:

``` 
...
ddr = 29, reg = 22
4660
addr = 29, reg = 23
4660
addr = 29, reg = 24
4660
addr = 29, reg = 25
4660
addr = 29, reg = 26
4660
addr = 29, reg = 27
4660
addr = 29, reg = 28
4660
addr = 29, reg = 29
4660
addr = 29, reg = 30
4660
addr = 29, reg = 31
4660
```

Things are likely working.

**Reference**

Used [https://www.freeformatter.com/html-escape.html](http://www.freeformatter.com/html-escape.html)

[link](http://en.wikipedia.org/wiki/Tux)