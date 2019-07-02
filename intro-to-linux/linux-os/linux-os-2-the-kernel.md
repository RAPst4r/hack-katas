The kernel is the core part of the Linux OS and the kernel is sometimes just referred to as “Linux”. It helps to manage the computer processor, the memory and the attached devices like your DVD drive, USB drive, keyboard, etc.
When hackers write hacker code that infects and corrupts the Linux kernel, it can lead to what is referred to as “Kernel Panic” and that is a serious threat.

To find out the name and details of a Linux operating system, you can use any of the following commands.
1. uname -r and uname -a
2. lsb_release -a
3. cat /etc/os-release
4. cat /proc/version
5. dmesg and grep

Let us try a few of the common Commands

In the terminal on your right, type
`uname`{{execute}} or `uname -s`{{execute}} and press enter  
You should see that the Operating System is __Linux__.    

Now try typing `uname -a`{{execute}} and press enter.  
You will see something like  
`Linux host01 4.4.0-151-generic #178-Ubuntu SMP Tue Jun 11 08:30:22 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux`  

This means that the name of the kernel is Linux  
The hostname is host01  
The numbers and text `4.4.0-XXX-generic` mean  
    4 - Kernel version  
    4 - Major version  
    0 - Minor version  
    XXX - Bug fix  
    generic - This is specific to a Linux distribution (or distro). In the case of Ubuntu, generic means desktop for the desktop version and server for the server version.  
The next text #178-Ubuntu means that this version of Linux kernel was compiled 178.  
The text `SMP Tue Jun 11 08:30:22 UTC 2019` is the latest timestamp when the kernel was compiled.  
The next three numbers, all of which in this case is `x86_64` represent  
the Machine architecture,  
the Processor architecture, and  
the Operating system architecture  
Finally the `GNU/Linux` means that the Operating System is Linux OS.  

You can also type `lsb_release -a`{{execute}} and press enter.  
You should see something like  
`Distributor ID: Ubuntu  
Description:    Ubuntu 16.04.6 LTS  
Release:        16.04  
Codename:       xenial`  
LSB stands for Linux Standard Base and  executing this command will give you more OS specific information such as the Distributor, Description the Release number and the codename that is used to refer to this version of the Linux OS.  

You can also use the following cat commands to find out information about the Linux kernel.  
The cat command stands for Concatenate (read) files and print to standard output (display on the screen)  
`cat /etc/os-release`{{execute}}  
`cat /proc/version`{{execute}}  

The last way that we will learn to find to find out kernel information is by using 2 familiar Linux commands - dmesg and grep.  
__dmesg__ is a command used to examine and display messages from the kernel and the  
__grep__ command searches and prints the lines matching a pattern.  
By combining these two commands we can we can print the kernel messages using dmesg and grep to find the pattern "Linux" in the messages.  
Try typing `dmesg | grep 'Linux'`{{execute}} and press enter.  
You should see some information about the Linux kernel.  
