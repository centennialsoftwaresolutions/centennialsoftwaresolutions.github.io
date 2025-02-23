# I2S audio output with a Raspberry Pi Zero W and AD SSM2518 DAC (PMOD AMP3)

![fragments_sans_centennial_animated](C:\Users\gensh\Desktop\New folder\fragments_sans_centennial_animated.gif)

## Raspberry Pi Zero W and AD SSM2518 DAC

This blog post shows how to enable audio output with a Raspberry Pi Zero W and AD SSM2518 DAC by configuring Linux & ALSA on a [<u><span>Raspberry Pi Zero W</span></u>](https://www.raspberrypi.com/products/raspberry-pi-zero-w/) to output audio via I2S to a [<u><span>Digilent PMOD AMP3</span></u>](https://digilent.com/reference/pmod/pmodamp3/start), which uses an SSM2518.

## Hardware setup

Configure the jumpers on the PMOD AMP3 as follows:

-   JP2: unset (BCLK = MCLK)
    
-   JP3: set (I2S mode)
    
-   JP4: set (BCLK = 256x Fs)
    
-   JP5: set (put DAC in stand-alone mode)
    
-   JP6: unset (0db gain)
    

The PMOD must be connected to the 40-pin header on the Pi. On the Pi header, the square pad is pin [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1) (3v3), adjacent to pin [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2) (5v). The next row of the header has pins [#3](https://www.centennialsoftwaresolutions.com/blog/hashtags/3) & 4, and so on.

The PMOD’s pinout is shown on its documentation page (linked above).

-   Connect pin [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1) (3v3) on the Pi to pin [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12) (Vcc) on the PMOD
    
-   Connect pin [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5) (GND) on the Pi to pin [#5](https://www.centennialsoftwaresolutions.com/blog/hashtags/5) or [#11](https://www.centennialsoftwaresolutions.com/blog/hashtags/11) on the PMOD
    
-   Connect pin [#12](https://www.centennialsoftwaresolutions.com/blog/hashtags/12) (BCM18) on the Pi to pin [#1](https://www.centennialsoftwaresolutions.com/blog/hashtags/1) (BCLK) on the PMOD
    
-   Connect pin [#35](https://www.centennialsoftwaresolutions.com/blog/hashtags/35) (BCM19) on the Pi to pin [#4](https://www.centennialsoftwaresolutions.com/blog/hashtags/4) (LRCLK) on the PMOD
    
-   Connect pin [#40](https://www.centennialsoftwaresolutions.com/blog/hashtags/40) (BCM21) on the Pi to pin [#2](https://www.centennialsoftwaresolutions.com/blog/hashtags/2) (SDATA) on the PMOD
    

## Environment setup

If you don’t already have your Pi running Raspbian, download the image from [https://www.raspberrypi.com/software/operating-systems/](https://www.raspberrypi.com/software/operating-systems/) (any version of the 32-bit image will be fine – desktop or lite), unxz it, and flash the .img file to a SD card.

The SD card should now contain a 512 MB FAT32 partition and a 2 GB ext4 root partition. Boot the Pi once to allow it to perform the initial one-time setup (set a username & password and expand the filesystem to fit the SD card).

## Configure device tree overlays

Edit the config.txt file in the FAT32 partition (on a running Raspbian system, that’ll be /boot/config.txt). Disable the built-in HDMI audio interface by commenting out the “dtparam=audio=on” line. Next, add to the file:

```
dtoverlay=ssm2518
dtoverlay=i2s-mmap
```

This will tell the Raspbian bootloader to load these dtbo (compiled device tree overlay) files and pass them off to the kernel while booting. The overlays add a simple-audio-card device for the ssm2518 chip linked to the Pi CPU DAI.

## Configure ALSA

In the ext4 partition on the SD card (the Raspbian rootfs), create /etc/asound.conf with this content:

```
pcm.ssm2518 {
type hw card 0
}


pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm “ssm2518”
channels 2
}
}

pcm.!default {
type plug
slave.pcm “dmixer”
}
```

This sets up an ALSA device corresponding to the simple-audio-card interface defined by the device tree. The dmix intermediary is necessary to allow multiple applications to use the device simultaneously. Finally, it configures the dmix to be the default output.

## Verify functionality

After a reboot, the new audio devices defined in asound.conf will be visible in alsamixer. Test audio output with speaker-test:

```
speaker-test -c2
```

This will alternate playing white noise on the left & right channels – speaker-test will print out which channel it’s currently playing on.

## References

-   ALSA logo from [<u><span>https://www.alsa-project.org/main/images/alsalogo.gif</span></u>](https://www.alsa-project.org/main/images/alsalogo.gif)
    
-   Raspberry Pi Zero W clipped from [<u><span>https://www.raspberrypi.com/products/raspberry-pi-zero-w</span></u>](https://www.raspberrypi.com/products/raspberry-pi-zero-w/)
    
-   Pmod AMP3 clipped from [<u><span>https://digilent.com/reference/pmod/pmodamp3/start</span></u>](https://digilent.com/reference/pmod/pmodamp3/start)
    

## Methods

The animated gif was built with Canva