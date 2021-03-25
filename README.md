Create a ramdisk device called mydisk. 

OS: minix-R3.3.0

Description:
- During boot 2 devices are created:
	- block device: "dev/mydisk" device with the size of (4 * 1024 * 1024) bytes is created.
	- character device: "dev/hex"
- Supports:
	- "dev/mydisk":
		- Mounting of the device
		- Writing to / Reading from the device 
	- "dev/hex":
		- Reading from the device as hex characters

MINIX 3 File Changes:
- minix/drivers/storage/memory/memory.c 
- minix/commands/MAKEDEV/MAKEDEV.sh
- minix/include/minix/dmap.h

Compiling Commands Within MINIX 3.3.0:
1. cd /usr
2. rm -r /src
3. git clone git://github.com/sorapk/minix.git src
4. cd /usr/src
5. make build > build.log
6. reboot

dev/mydisk testing commands:
1. mkdir /mnt/mydisk
2. chmod 755 /mnt/mydisk
3. mkfs.mfs /dev/mydisk
4. mount /dev/mydisk /mnt/mydisk
5. cd /mnt/mydisk
6. seq -s '' 500000 > data
7. vi data
8. df
9. ls -l /dev/mydisk