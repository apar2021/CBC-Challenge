# Task 3 - Analyze the Firmware - (Emulation)Points: 200
Leveraging that datasheet enabled you to provide the correct pins and values to properly communicate with the device over UART. 
Because of this we were able to communicate with the device console and initiate a filesystem dump.
To begin analysis, we loaded the firmware in an analysis tool. 
The kernel looks to be encrypted, but we found a second-stage bootloader that loads it. 
The decryption must be happening in this bootloader. There also appears to be a second UART, but we don't see any data coming from it.

Can you find the secret key it uses to decrypt the kernel?

Tips:

You can emulate the loader using the provided QEMU docker container. One download provides the source to build your own. The other is a pre-built docker image. See the README.md from the source download for steps on running it.
Device tree files can be compiled and decompiled with dtc.

Downloads:

U-Boot program loader binary (u-boot.bin)
Recovered Device tree blob file (device_tree.dtb)
Docker source files to build the QEMU/aarch64 image (cbc_qemu_aarch64-source.tar.bz2)
Docker image for QEMU running aarch64 binaries (cbc_qemu_aarch64-image.tar.bz2)
Prompt:

Enter the decryption key u-boot will use.

Comments: I think anyone who did Task 3 knows from experience that the answer was primarily there and we pretty much ran circles around it half the time. 
# Problem Solving Approach 
While booting up the QEMU emulator for the Raspberry PI device, we are loaded into the bootloader which lists environment variables as well as commands we can run inside of it. 
While parsing through our environment variables, we can find our answer in this case by reading memory at memory locations designated by the bootloader env vars. 
