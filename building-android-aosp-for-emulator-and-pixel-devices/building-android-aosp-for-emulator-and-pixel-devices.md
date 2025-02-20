# Building Android (AOSP) for emulator and Pixel devices

This article will show you how to:

-   build Android for an emulator target
    
-   build Android for a real hardware target
    
-   run the build in an emulator
    

## Prerequisites & environment setup

(Google docs: https://source.android.com/docs/setup/start/requirements)

Google says you can use Ubuntu 18.04+ for Android development. You can use a lightweight LXC container to get an Ubuntu environment regardless of your native Linux distribution. Using a container also helps prevent any conflicts between environment setup required for other development work you’re doing on the host OS. Refer to [<u><span>our article on LXC setup</span></u>](https://www.centennialsoftwaresolutions.com/post/set-up-lxc-for-vitis-vivado-and-petalinux-development) for more information.

Google says you’ll need 400 GB of disk space and 64 GB of RAM. Their 72 core x 64 GB machines take 40 minutes for a clean build, and their 6 core x 64 GB machines need 6 hours to do a build.

Install prerequisites: (run these commands in the LXC container, or the host OS if you’re using native Ubuntu)

```
sudo apt update
sudo apt upgrade

sudo apt install git-core gnupg flex bison build-essential zip curl zlib1g-dev libc6-dev-i386 libncurses5 x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig

sudo apt install repo
```

Repo is AOSP’s wrapper around git. See the Google docs for more info: https://source.android.com/docs/setup/create/coding-tasks

Also, install adb and fastboot:

```
sudo apt install adb fastboot
```

## Download the AOSP source and binary blobs

https://source.android.com/docs/setup/download/downloading

```
mkdir android
cd android

repo init -b main -u https://android.googlesource.com/platform/manifest
```

Instead of `-b main`, you can do something like `-b android-14.00.0_r1` to check out a specific version of Android. See https://source.android.com/docs/setup/reference/build-numbers#source-code-tags-and-builds for a list of tag names.

The above commands will set up a repo project. Run repo sync to download the files.

```
repo sync -c -j$(nproc)
```

This took about 40 minutes total on a ~450 Mbit/s internet connection. The download size was just under 100 GB, and the unbuilt project uses ~200 GB of disk space.

This is not required, but you can use GPG to verify your downloaded project against Google's key. Refer to Google's documentation for more info on that: https://source.android.com/docs/setup/download/downloading#verifying-git-tags

### Binary blobs

The default AOSP build can run in an emulator, but additional binary blobs are needed to run on actual hardware. Google distributes the blobs for their hardware:

-   If using the main branch: [https://developers.google.com/android/blobs-preview](https://developers.google.com/android/blobs-preview)
    
-   If using another release: [https://developers.google.com/android/drivers](https://developers.google.com/android/drivers)
    

These files are 300-500 MB.

Using the Pixel 7 (panther) as an example:

Download the .tgz file for your target and extract it to get a shell script:

```
tar -xzf google_devices-panther-….tgz
```

This will extract a shell script: ./extract-google\_devices-panther.sh

If you’re not already in the AOSP project folder (where you ran \`repo init\` and \`repo sync\`) move the .sh script into the project folder. From the AOSP project folder, run the script:

```
./extract-google_devices-panther.sh
```

Accept the license. A new \`vendor\` folder is created and contains the blobs.

## Build Android

```
source build/envsetup.sh
```

Select a build target with \`lunch\`. The \`cf\_x86\_64\_phone\` target is for the Cuttlefish emulator, whereas \`panther\` is a Pixel 7.

```
lunch aosp_cf_x86_64_phone-trunk_staging-eng
lunch aosp_panther-trunk_staging-eng
```

Instead of `...-eng`, you can use the `user` or `userdebug` build variants instead: https://source.android.com/docs/setup/create/new-device#build-variants

You can run just \`lunch\` to get a list of all available build targets.

Run m to do the build:

```
m
```

Building Android can take a few hours, depending on your hardware. When the build is complete, the output products (.img files) will be available in out/target/product/vsoc\_x86\_64 or out/target/product/panther (this directory will be available in the $OUT environment variable after you run lunch).

## Launch the emulator

The acloud tool manages Android virtual devices (emulators). It can run AVDs locally or on Google Cloud instances.

Ensure you’ve done \`source build/envsetup.sh\` and \`lunch <target>\` in the terminal session you’re running acloud in.

First, do its one-time setup:

```
acloud setup
```

And reboot. Next, create a local AVD from the current project build:

```
acloud create --local-image –local-instance
```

This will open up a VNC viewer window with your Android build. You should also be able to connect to the AVD with adb – e.g. \`adb devices\`, adb shell\`.
