How to Build
====================
**This short guide assumes you're on Ubuntu 11.04 or above** and have your Android build enviroment setup already.

Getting SimplicityXL Kernel source & tools
-------------------------------------------

First, we need to create directories for the build so open Terminal and issue the follow commands:

    $ cd 
    $ mkdir -p ~/Android
    $ cd Android
    $ mkdir Kernel
    $ cd Kernel
    $ mkdir Device
    $ cd Device
    $ mkdir LG870
    $ cd LG870
    $ mkdir SmpXlKernel
    $ cd SmpXlKernel

    $ git clone https://github.com/chevanlol360/Simplicity_kernel_Fx1_LG870

Now that you have the kernel source, you need to get toolchains:

    $ cd /Android/Kernel
    $ mkdir toolchains
    $ git clone https://github.com/chevanlol360/android_prebuilt_toolchains

Compiling Kernel
====================
Issue the following commands to build the kernel

    $ cd
    $ cd Android/Kernel/Device/LG870/SmpXlKernel/Simplicity_kernel_Fx1_LG870
    $ export ARCH=arm
    $ export CROSS_COMPILE=~/Android/Kernel/toolchains/android_prebuilt_toolchains/arm-eabi-linaro-4.6.2/bin/arm-eabi-
    $ make clean 
    $ make 1chaos_defconfig
    $ make menuconfig

Continue Issuing commands

    $ make -j4
    

When its done you'll find your zlmage under /arch/arm/boot Grabbed stock kernel from your phone and unpack the boot.img with Android Kitchen then go inside the unpacked folder and replace the zlmage in the folder with the one you just built. Then go back to the Simplicity Kernel Directory and copy the folder called "boot.img-ramdisk" and then go back to the Android Kitchen folder then go inside the unpakced folder again and delete the Folder inside called "boot.img-ramdisk" and then paste the folder you just copied from the kernel directory. Then Repack the boot.img with Android Kitchen and continue below.

Loki'ing
====================
Issue the following commands to loki your kernel
    
    $ cd
    $ cd Android
    $ mkdir Loki
    $ cd Loki
    $ git clone https://github.com/chevanlol360/loki
    
Go inside the Loki folder and doubble click on the run.sh file and open it with terminal and when its done a new file called smpboot.loki will be the output flash it to your device.  
