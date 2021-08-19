# linux-from-scratch
Going through this guide because I am a noob: https://www.linuxfromscratch.org/


My thoughts going through LFS
========================================

I'm doing all of this on Ubuntu 20 LTS.
`env-bootstrap.sh` installs missing packages specified on https://www.linuxfromscratch.org/lfs/view/11.0-rc1/chapter02/hostreqs.html

`version-check.sh` checks if packages are installed or not 

Getting Started with the Book
-----------------------------
Having discovered technical specifications of the Linux Filesystem, I ended up not going through the book at all. 

https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html (Filesystem hierarchy standard - defines the directory structure and directory contents in Linux distribution) 
https://refspecs.linuxfoundation.org/lsb.shtml (Software system structure standard - defines how standard libraries work with filesystem hierarchy and kernel. I think. Probably more. I'm just learning here, so mansplain away!)
https://pubs.opengroup.org/onlinepubs/9699919799/ (Portable Operating System Interface - defines APIs at the system and user level)

```bash
sudo apt-get install bison
sudo apt-get install gawk
sudo apt-get install m4
sudo apt-get install texinfo
```

Day2 - Preparations
-----------------
Time: 30 min

### Preparing a new partition
With `sudo cfdisk` i have created 3 partitions:
* 100MB boot partition, that is supposed to be mounted to /boot
* 8GB root partition
* 400MB swap partition

And then with:
`
sudo mkfs sda1 -t ext2
sudo mkfs sda2 -t ext3
sudo mkswap ext3
`
i created filesystems.

`debugfs -R sdaX` showed me exactly what it shoud.. I'm glad, that ubuntu's makefs didn't gave me some addition problems. After i mounted sda1 to %LFS and sda2 to %LFS/boot i used wget list for download packages and other sources.