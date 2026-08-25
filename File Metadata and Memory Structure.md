* Master Boot Record and GUID Partition Table are partitioning schemes for disks on the first sector of the disk.
	* Often target for Bootkits
#### Boot Process
* After power is introduced, the hardware components are initialized, the OS is loaded into memory, and the user can then interact
	1. Post check after power
		* Power to CPU allows BIOS/UEFI to run instructions using power form CPU
			* BIOS is legacy and has size limitation
				* uses MBR scheme
			* UEFI is a replacement for BIOS with up to infinite size and secure boot
				* redundancy through recovering backups despite boot code being corrupted
			* The beep when powering is the Power on Self Test for hardware components
		* 
	2. Locates bootable
	3. Reads partition
	4. Loads bootloader
	5. Loads OS
### MBR
* Made of sectors (512 bytes) viewable in a hex-editor
* Structure of MBR:
	* Bootstrap code (446 bytes)
		* finds bootable partition from table
	* Partition Table (64 bytes)
		* finds OS partition
		* loads OS kernel
	* MBR Signature (2 bytes)
	* Total of 4 partitions
* |Bytes Position|Bytes Length|Bytes|Field Name|
	|0|1|80|Boot Indicator|
	|1-3|3|20 21 00|Starting CHS Address|
	|4|1|07|Partition Type|
	|5-7|3|FE FF FF|Ending CHS Address|
	|8-11|4|00 08 00 00|Starting LBA Address|
	|12-15|4|00 B0 23 03|Number of Sectors|
* Logical Block Addressing is the logical start of the partition
* Depending on the partition, bytes are stored as little-endian where the Least to Most signifigant Byte is
	* must reverse to use
	* multiple by sector size (512)
* All MBR's are signed with the magic number 55 AA
* Reading hexadecimal for partitions
##### Threats of MBR:
* Since MBR executes before OS, it can bypass OS protection, persisting throuhg removal of OS and 
### GPT Partitions
1. Protective MBR
	* BIOS FIrmware may still be used, but now using GPT partitions
	* Bootloader code and Partition Table major parts of MBR
	* MBR Signature
2. Primary GPT Header (after MBR signature)
	* First 92 bytes; rest are zeroes
	* Start of GPT header: 45 46 49 20 50 41 52 54
3. Partition Entry Array
	* Sector 2 can have total of 128 partitions
		* each partition is shown as 128 bytes
4. Backup GPT Header
5. Backup Partition Entry Array

* .efi files of GOT bootloader code is used to run before OS protections (bootkit), while secure boot verifies the integrity of boot files beforehand (use secure boot)