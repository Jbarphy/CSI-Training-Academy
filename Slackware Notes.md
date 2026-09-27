Concerns of Linux kernel adaptability to various hardware without manual configuration has been alleviated
* Automatic kernel detection of hardware
- Helpful to know
	- Partition sizes, layouts
	- Network Config
		- adapter, Network Mgt
	- Motherboard support
- Goal of learning Operating System
- File System and Configurations are left to be manually done, leaving automatic changes hampering investigations to be little

#### Slackware Disk and Naming Conventions
- A root partition is the main operating system files and directories
- Swap partitions are extension of RAM through virtual memory
	- Used when Physical RAM is full or pre-allocated completely
- Ideal to have both in tandem
- Useful to know whether fdisk, gdisk, or other partition is going to be used
- Interestingly, compared to other linux distros that boot into a installer program, Slackware uses an installer that is in a limited linux distro directly loaded into the system's RAM
- fdisk supports typical legacy FAT partition types while gidsk supports a GUID partition table
  	- Because we are using a partition that does not exceed 50 and learning a common yet equally ancient, I configured fdisk at boot for this project environment.
 
#### Partitioning
- After going through selecting our disk to be partitioned, I researched how disks are named in a distro like Slack, even though it seems to be like other linux distros
	- list fdisk with `fdisk -l`
 	-  	selected disk and created a system disk and swap partition
  		-swap partitions are virtual memory that dedicates pages less used by the OS to disk directly (highly volatile due to OS) annd useful for intense amounts of installers and packages being loaded
	- I also created a home partition that will need to be chagned to "home" after reboot and formatting
	  - reboot allows kernel to read partitions to disk
   - never used a curses menu before
   - choose ext4 for format type
