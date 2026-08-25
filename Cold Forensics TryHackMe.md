* Cold Forensics handles turned off or inactive machines
	* Response to **Cold Boot Attack**
		* RAM persists after being "cold", and allows quick startup for compromise
	* Exceeds memory forensics, and pursues other things like entire storage drives, peripherals, hardware configs, and residual data in volatile memory
	* Preserves integrity of data without writing over "hot" drive

* Order of Volatility: most to least
	1. CPU Registers and cache: lost once host is powered down
	2. Routing table, ARP Cache, Process Table, Kernel Stats, RAM: Reveals running processes and network connections; useful for finding malicious threats
	3. Temporary File Systems: Data in temp files are cleared on reboot; recently accessed files applications
	4. Hard Disk: Less volatile but still suspect to alterations and overwrites
		1. Imaging disk provides comprehensive snapshot of stored data, including deleted files or fragments
	5. Remote Logging and Monitoring Data: stable files that provide records of network activity and system events over time
	6. Physical Configuration and Network Topology: Documentation of data helped understand infrastructure and context of investigation
	7. Archival Media: Stored offline such as tapes and optical disks
* Methods of Data Acquisition:
	* Disk Imaging
	* Physical Imaging: 
		* Chip-off forensics: removing storage ship and read special equipment
		* JTAG Forensics: Uses Joint Test Action Group interfaces to access data form embedded systems; helpful for mobile or IoT devices

* Important considerations of Storage:
	* Keep data at rest encrypted 
	* Allow only those part of the investigation (Access Control Mechanisms)
	* Secure environment
	* Regular Audits of storage environment and access logs for compliance with security policies and potential breaches.
* Tools to consider using:
	1. Disk Imaging
		1. dd and dc3dd
		2. Guymager
		3. FTK Imager
	2. Disk Image Analysis
		1. The Sleuth Kit
		2. Autopsy
		3. EnCase Forensic
		4. FTK
		5. Magnet AXIOM
		6. Bulk Extractor
		7. X-Ways Forensics

Workflow of Disk Image Analysis:
* Load Disk Image
* Run Initial Processing: parse, identify artifacts, build indexes, extract metadata
* Conduct Artifact Analysis: Keyword search, hash comparison, registry parsing, web history recovery, and artifact specific modules
* Recover Deleted files: file carving and unallocated space to recover deleted space
* Bookmark and Report: Tag relevant evidence, take notes, generate reports with metadata and timelines
Techniques for Disk Image Analysis:
* Mounting creates virtual drive with ability to explore file structures without altering original image
	* Mount images in read-only mode or forensics environment
	* Extracting key digital artifacts
		- User documents and downloads
		- Registry entries (Windows)
		- Application and system logs
		- Email archives
		- Browser history and cache
		- Installed programs and executables
	- Recover deleted data using file carving for headers and footers to reconstruct files from raw data
	- Log All actions taken
	- Document analysis steps, tool versions used, timestamps, extracted artefacts, and chain of custody
