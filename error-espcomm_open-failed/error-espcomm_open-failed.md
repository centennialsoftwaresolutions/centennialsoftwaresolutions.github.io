# error: espcomm_open failed

![arduino_logo](arduino_logo.png)

This post shows a solution to the **espcomm\_open failed** error after clicking **Upload** on Linux. It also shows how to cause this error.

**<u><span>Symptom</span></u>**

After clicking **Upload** you see this error:

Arduino: 1.8.7 (Linux), Board: "WeMos D1 R2 & mini, 80 MHz, 921600, 4M (3M SPIFFS)"

Sketch uses 225289 bytes (21%) of program storage space. Maximum is 1044464 bytes.

Global variables use 32140 bytes (39%) of dynamic memory, leaving 49780 bytes for local variables. Maximum is 81920 bytes.

warning: espcomm\_sync failed

**error: espcomm\_open failed**

**error: espcomm\_upload\_mem failed**

**error: espcomm\_upload\_mem failed**

This report would have more information with

"Show verbose output during compilation"

option enabled in File -> Preferences.

**<u><span>A Solution</span></u>**

1\. Open a terminal

2\. Type **fuser /dev/ttyUSB0**

You should see something like:

/dev/ttyUSB0: 28988

3\. Type **kill -9 28988** (replace 28988 with the actual number listed)

4\. Click **Upload** again

You should see something like:

Sketch uses 225289 bytes (21%) of program storage space. Maximum is 1044464 bytes.

Global variables use 32140 bytes (39%) of dynamic memory, leaving 49780 bytes for local variables. Maximum is 81920 bytes.

Uploading 229440 bytes from /tmp/arduino\_build\_91017/sketch\_nov03a.ino.bin to flash at 0x00000000

................................................................................ \[ 35% \]

................................................................................ \[ 71% \]

................................................................. \[ 100% \]

**<u><span>Cause Problem</span></u>**

In another terminal type minicom (follow \[[<u><span>link</span></u>](https://www.centennialsoftwaresolutions.com/blog/configure-minicom-for-a-usb-to-serial-converter)\])

Click Upload, you'll see the error

**<u><span>Reference</span></u>**

Arduino icon clipped from \[[<u><span>link</span></u>](https://www.arduino.cc/)\]