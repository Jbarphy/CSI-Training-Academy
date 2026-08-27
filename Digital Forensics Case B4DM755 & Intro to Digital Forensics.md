How should the police collect evidence from devices? What procedures should they follow?
How can one transfer the digital evidence? What are the best practices?
How can one analyze collected digital evidence? Personal storage varies?

Chain of Custody Details: 
1. Special handling of evidence and devices
2. Establish chain of custody
3. Place evidence in secure containers (such as the network)
4. Transport
 
 Metadata includes things like file creation date, modify date, title, subject, author, creator, and others
 * For example, pdf and word doc contain this metadata

In the real world, in order for investigators to do just about anything, there must appropriate preparations and legal justifications for their actions. 
In this case, there are some unique requirements:
1. Documentation must reflect the material in inventory and what the purpose of it is, while maintaining the integrity of the evidence
2. Hashes and copies of the files must be maintained, with the least amount of tampering possible to the original copy
3. No shutdown procedures other than manual power disconnection, to prevent counter-measures for anti-forensics
4. Any forms containing Chain of Custody must be complete ASAP and throughout the investigation
5. When first investigating a crime scene, any computers require:
	1. Image of RAM offline
	2. Checking for evidence of drive encryption
	3. Take image of drive(s)

In this sample case, FTK Imager was used to examine the flash drive in question. The elements of which to know are:
* Evidence Tree Pane
* File List Pane
* Viewer Pane
The goals of using tools like FTK imager is to manipulate nothing of the original while securing a pure, unaltered copy for evidence and analysis.
1. Verify encryption
2. Obtain forensic image of disk
3. analyze recovered artifact

We already know some details of the case, namely that the suspect encrypted the drive using NFTS EFS (AWS Elastic File System) instead of FAT32 and exFAT
* We can use FTK to detect EFS Encryption, however that is only one option of Encryption, others being Veracrypt and Bitlocker

We then use FTK to create a forensic image of the physical drive and ensure that the image is verified and creates a directory of all files in the image (in order to replicate the file structure completely). 
* Ensure that either dd or dc3dd is used for the image type.
* Selecting verify will use hashing to determine if the raw image is the same hash as the original

Next, the forensic image will need mounted in order to begin extracting artifacts
- After mounting it pays to look for any manipulation and file details
	- Deleted files (x's)
		- export these files for further review
	- corrupted files (0 file size)
	- evidence of obfuscated files (conflicting headers, metadata, and extensions)