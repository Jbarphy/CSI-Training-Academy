Useful tools:
1. dd for acquisition and carving of files
2. grep to examine and find file structures
3. file + xxd for signature identification and analysis
4. awk as a text extractor
5. sed that reads data line by line using scripts commonly used for substitutions and filtering/deleting of data
* Learn to not rely on GUI for analysis and tool usage
* su + - applies root path, meaning you dont have to enter full path for changing directories
* Learn how OS, kernel, Hardware, or software interact with each other when conducting investigations
	* lspci shows attached devices to PCI bus +k for kernel module version
	* lsusb for use adapters
	* kernel is how hardware is controlled through software and resources of the computer
		* drivers are the software controlling your hardware
* Device nodes are the files representing devices in /dev directory
	* was static before udev
	* Udev creates nodes actively as kernel detects devices and populates /dev then
	* does not automount or interact with applications directly, simply kernel to hardware
	* research startup scripts for daemons and directory discovery
	* as such disk and drives are seen as files in linux under the /dev directory
* CD ROM or DVD shown as srx in dev, while sdb is a USB (not SATA)
	* lsblk to show disks , mount points, and partitions
	* lsscsi for detailed disk info minus partitions
	* drive can be referenced using volume label, UUID, kernel path instead of device node assignment
	* fdisk to show or create disk partitions
* dmesg command show kernel messages indicating device connection
	* tail -f /var/log to show messages after plugging in device
* Mounting manually allows a temp source for images
	* mount -t [filesystem] -o [options] [device] [mountpoint]
	* -t is the file system type:
		* lsbllk -f -> file -s dev/[device] for file system
		* file uses signature for file system signing
	* You can use findmnt -real for any mount points and system types
	* Mounting for compute start files through /etc/fstab
	* understand the configuration of mounting for your environment
Useful commands:
ps ax: all processes, even without terminal
find [directory] -[iname or name] [filename]
**mess with vimtutor or whatever kali has**
