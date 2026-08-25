* system and user-level data while computer runs
* Stores information with balancing speed and cpacity
	* CPU Registers -> CPU Cache -> RAM -> Disk Storage
* Virtual memory is assigned memory from the operating system to physical hardware such as RAM or swap if needed
	* swaps are reserved areas on the disk that OS use to store data from RAM when physical memory is temporarily full.
* RAM: 
	* kernel space: reserved for OS and low level services such as drivers and memroy access
	* user space: processes launched by users or apps with separate space for each unique to the user
	* User process is structured through:
		* Stack: temp data like function arguments and return addresses dynamically
			* shell commands normally on stack
		* Heap: dynamic memory allocation during runtime such as objects and buffers
			* encryptions keys are often here
		* Executable: stores actual code or instructions for CPU to run
		* Data sections: space to store global variables and other data needed to execute
	* Snapshots of RAM reveal running processes, loaded executables, open network connections, user info, recent commands, decrypted content and injected code and fileless malware
* Memory Dumps
	* Full memory dumps capture all RAM including user and kernel space
	* Process dump: captures memory of single running process
	* Pagefile and Swap Analysis: memory assigned to disk when RAM is full containing fragments of RAM and context
	* Hibernation files can be parsed to extract RAM contents saved to machine when entering hibernate mode
### Volatility
* WinPmem: drive based tool that acquires RAW/ELF formats and embeds acquisition metadata for chain of custody
* Magnet RAM capture: Gui driven snapshot of volatile memory on live windows hosts while minmising footprint to host
* AVML: dumps memory into compressed ELF file without requiring kernel module
* LiME: Loadable Kernel module capturing full volatile memory over disk or network
* OSXPmem: Pmem fork to create raw memory images on Macs
* Virtual environments memory files are different for vm specific drives:
	* - VMware - `.vmem`
	- Hyper-V - `.bin`
	- Parallels - `.mem`
	- VirtualBox - `.sav`
- common plugins for V are
	- windows.info
	- linux.info
	- pslist
	- pstree
- https://blog.onfvp.com/post/volatility-cheatsheet/