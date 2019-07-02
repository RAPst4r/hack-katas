The Bootloader is what makes the computer start (or boot) up. You may be used to seeing a splash screen show with a message like “Your computer is starting up”. When this splash screen is shown, the bootloader part of the OS is running in the background, making your computer ready for your use. The bootloader is part of the __Master Boot Record__ __(MBR)__ portion of the OS. What the bootloader does is - it loads the Operating System into computer memory.  

Common Linux bootloaders include:  
- GRUB (GRand Unified Bootloader)  
- LILO (Linux Loader)  
- Syslinux which is really a mix of many lightweight bootloaders that makes it possible for you to boot from different sources, such as optical disks like CDs, DVDs, USBs or from a network.  

To find out what bootloader, you Linux OS uses, you can use the `file -s` command.
But before you can find out the bootloader, we must first find out what the bootdisk is. The boot disk has the __Master Boot Record__ (MBR)  
To find of the bootdisk, you will need to use the `fdisk -l` command  

Type `fdisk -l`{{execute}} and press enter  
You should see something like  
`Device     Boot    Start       End  Sectors  Size Id Type
/dev/vda1  *        2048  94160895 94158848 44.9G 83 Linux
/dev/vda2       94162942 102397951  8235010  3.9G  5 Extended
/dev/vda5       94162944 102397951  8235008  3.9G 82 Linux swap / Solaris`

The one with the __asterisk__ (__`*`__)  is the bootdisk. In the example above, it is `/dev/vda1`  

Now type `file -s /dev/vda1`{{execute}} and press enter. The `-s` option stands for special files and the bootloader is a special file in the Linux OS. This command will give you information as to what bootloader is.
In this case, you may see something like
`/dev/vda1: Linux rev 1.0 ext4 filesystem data, UUID=50300c45-9dcd-483c-acea-2f376f7acd95 (needs journal recovery) (extents) (large files) (huge files)`
which does not explicit state the name of the bootloader.

So what we can do is use the dmesg and grep command and search for the word BOOT  
Type `dmesg | grep BOOT_IMAGE`{{execute}} and enter. This will search for the word BOOT in the kernel messages and output the BOOT_IMAGE details.   
When you run the `dmesg` command  
You should see something like  
`[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-151-generic root=UUID=50300c45-9dcd-483c-acea-2f376f7acd95 ro quiet
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-151-generic root=UUID=50300c45-9dcd-483c-acea-2f376f7acd95 ro quiet`  

Notice in the Kernel command line, you see the words `BOOT_IMAGE=/boot/vmlinuz-4.4.0-151-generic`  
The Linux Loader (LILO) always passes the word `BOOT_IMAGE=[KernelName]` to the kernel, where `[KernelName]` is the name by kernel.  
From this you can determine the the bootloader used here is LILO.  

From a hacker perspective, it is important to recognize that Bootloader computer viruses corrupt the bootloader part of the OS making it impossible for the computer to start, causing a denial of service or DoS attack.   
