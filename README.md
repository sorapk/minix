Create a ramdisk device called mydisk. 

OS: minix-R3.3.0

Description:
- During boot, "dev/mydisk" device with the size of (4 * 1024 * 1024) bytes is created.
- Supports:
	- Mounting of the device
	- Writing to / Reading from the device 

MINIX 3 File Changes:
- minix/drivers/storage/memory/memory.c 
- minix/commands/MAKEDEV/MAKEDEV.sh
- minix/include/minix/dmap.h

Compiling Commands Within MINIX 3.3.0:
1. cd /usr
2. git clone git://github.com/sorapk/minix.git src
3. cd /usr/src
4. make build > build.log
5. reboot

Mydisk Testing Commands:
1. mkdir /mnt/mydisk
2. chmod 755 /mnt/mydisk
3. mount /dev/mydisk /mnt/mydisk
4. mkfs.mfs /dev/mydisk
5. mount /dev/mydisk /mnt/mydisk
6. cd /mnt/mydisk
7. seq -s '' 500000 > data
8. vi data
9. df
10. ls -l
