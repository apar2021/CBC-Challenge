# Task 4 - Emulate the Firmware - (Dynamic Reverse Engineering, Cryptography) Points: 500
We were able to extract the device firmware, however there isn't much visible on it. All the important software might be protected by another method.

There is another disk on a USB device with an interesting file that looks to be an encrypted filesystem. Can you figure out how the system decrypts and mounts it? Recover the password used to decrypt it. You can emulate the device using the QEMU docker container from task 3.

Downloads:

main SD card image (sd.img.bz2) USB drive image (usb.img.bz2) Linux kernel (kernel8.img.bz2) Device tree blob file for emulation (bcm2710-rpi-3-b-plus.dtb.bz2) Prompt:

Enter the password used to decrypt the filesystem.

# Mistakes
The problem that I had while doing this Task was the amount of unncessary time I spent on it. In this task, I found my answer and was shuffling around the answer many times. I found the output of running hashcat appended to the end of my output.txt which contained 10 lines of the same hashcat output.

# Problem Solving Approach
In order to find the encrypted partition, we have to extract the files from the USB drive image. 
From the USB drive image, we can find artifacts for the encrypted partition and find clues regarding its password. 
After extraction, we have found the encrypted partition and we have a file called mount_part that denotes how to mount the encrypted partition. We are introduced to a LUKSv1 partition that essentially is very secure. 
To find out more information about the partition, we can dump the header of the partition. From the header, we can see its hash spec, as well as other information. 
The header comes into relevance in the next couple of steps. From the file mount_part, we can see that passphrase in this case is the hostname followed by 3 unknown characters appended from id.txt referenced and SHA1 hashed. 
Hostname in my case was overtmath. I used Crunch to generate password lists given this information. 
That generated a file of over 1 million lines. I needed to reduce my search time so I looked at referenced id.txt in the file mount_part. 
In the file, after hexdumping it, we can see that the file is padded. The file is otherwise unable to be read and seems to be corrupted. 
After investigating the id.txt, we find that the text is 32 bytes long and could potentially be a hexadecimal string. 
We adjust the search space and append characters from Crunch's charset hex-lower to generate a password list of 4096 passwords. 
Using the password list, we can use this to bruteforce the encrypted partition using hashcat.
