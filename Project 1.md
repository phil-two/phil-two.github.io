For those who don’t know markdown, here is a cheat sheet: [https://www.markdownguide.org/cheat-sheet/](https://www.markdownguide.org/cheat-sheet/)

# 

# Project 1 \- Arch Linux

## **Pre-Installation**

1. Type cat /sys/firmware/efi/fw\_platform\_size  
2. You should get 64, I originally struggled and got a null return, I figured it out by changing settings while creating the VM  
3. Type fdisk \-l (Should return /dev/sda)  
4. Use fdisk and the disk found using the above and type fdisk /dev/sda  
5. Go through fdisk and create 2 partitions  
6. Format the partitions. One should be fat32 and the other should be ext4  
7. Type mkfs.fat \-F 32 /dev/sda1 and mkfs.ext4 /dev/sda2  
8. Now mount the system with mount  
9. Type mount /dev/sda2 /mnt and mkdir /mnt/boot /mnt/var /mnt/home and mount /dev/sda1 /mnt/boot

## **Installation and Configuration**

1. Install packages by typing pacstrap \-K /mnt base linux linux-firmware  
2. Now type genfstab \-U /mnt \>\> /mnt/etc/fstab  
3. Check this file by typing nano /mnt/etc/fstab  
4. Type arch-chroot /mnt to change root into the new system to configure and localize it  
5. I did the Time and Localization in reverse order as I found it easier.  
6. Type ln \-sf /usr/share/zoneinfo/America/Chicago /etc/localtime but replace America/Chicago with your region and city  
7. Type hwclock –systohc –utc (I added the –utc to ensure it was set correctly)  
8.  nano /etc/locale.gen and find en\_US.UTF-8 UTF-8 or your corresponding locale  
9. Type echo LANG=en\_US.UTF-8 \> /etc/locale.conf  
10. Type export LANG=en\_US.UTF-8  
11. Set the hostname to archlinux by typing echo archlinux \> /etc/hostname  
12. Type systemctl enable dhcpcd to complete network configuration  
13. Type mkinitcpio \-P  
14. Now set the root password and create users  
15. Type passwd root and set the root password  
16. Now type useradd \-m \-g users \-G wheel \-s /bin/bash phil  
17. Repeat the above step but replace phil with justin and codi  
18. Type passwd phil and set the password  
19. Repeat the above and set the password to GraceHopper1906  
20. Type nano /etc/sudoers and add phil ALL=(ALL:ALL) ALL and repeat for the above names to give them sudo  
21. Type exit to leave the system configuration  
22. Type umount /mnt/boot and umount/mnt  
23. Type reboot  
24. When you reenter, type sudo pacman \-Syy  
25. Type sudo pacman \-S openssh to install ssh  
26. Type sudo pacman \-S zsh to install a new shell  
27. Type sudo pacman \-S \--needed lxqt xdg-utils ttf-freefont sddm xorg firefox vlc filezilla leafpad xscreensaver archlinux-wallpaper to install LXQT and all the needed components  
28. Restart because you get an error that you are out of space  
29. After several rounds of this attempt to clear space on your laptop as you believe that is the issue  
30. It is not the issue  
31. Enjoy the Arch Linux experience

Documentation Completed by:   
Philip Tu  
