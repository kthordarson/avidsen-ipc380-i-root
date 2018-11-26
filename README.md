# avidsen-ipc380-i-root
How to root the Avidsen ipc380 / goke gk7102s
![](https://github.com/kthordarson/avidsen-ipc380-i-root/blob/master/20181124_180107.jpg)

Connect to the UART ports on the PCB with your favorite usb-uart thing. Set serial speed to 115200-8n1. 
Quickly press any key to interrupt the boot and drop into u-boot console. 
From here set the boot parameters for the linux kernel. Use the command editev to add "single" to the bootarg variable and then type boot and press enter to boot into single user linux mode.

You now have full access to the filesystem and can edit /etc/passwd and /etc/shadow to add a new root user or clear the existing password.
 
If you have previously configured wifi, dump the entire flash to a tftp server with the following commands:

>tftp -l /dev/mtd0 -r uboot.img -p <your tftpd>
  
>tftp -l /dev/mtd1 -r ubootenv.img -p <your tftpd>
  
>tftp -l /dev/mtd2 -r kernel.img -p <your tftpd>
  
>tftp -l /dev/mtd3 -r rootfs.img -p <your tftpd>
  
>tftp -l /dev/mtd4 -r all.img -p <your tftpd>


Have fun.
