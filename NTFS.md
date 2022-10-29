#NTFS

NTFS (New Technology File System) uses clusters of blocks and file allocation tables, and is more complex and powerful than FAT32. 

Improvements and Refinements of NTFS:
* redundancy
* security: uses ACL (Access Control List) to specify the file permissions of a user. 
* compression
* encryption: uses EFS (encrypting file system)
* disk quotas: setting limits on drive space usage for users
* cluster sizing

To find what version of NTFS we are running use: ```fsutil fsinfo ntfsinfo```

### NTFS Structure
* NTFS uses an enhanced file allocation table called master file table (MFT). NTFS keeps a copy of the most critical parts of the MFT in the middle of the disk, reducing the chances that a drive error can wipe out both the MFT and the MFT copy. The MFT is usually near the front shown in the image below.

![MFT](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi2.wp.com%2Fknowitlikepro.com%2Fwp-content%2Fuploads%2F2020%2F05%2F9.png%3Fresize%3D693%252C524%26is-pending-load%3D1%23038%3Bssl%3D1&f=1&nofb=1&ipt=e4d40428ea7b5b470fd83237b4fb22d04c15d4ae7b3bcf20e446ca187326948a&ipo=images)

###Cluster Size

| Drive Size    |NTFS Cluster Size |  
| ------------- |:----------------:|
|7 MB to 16 TB  | 4KB
|16 to 32 TB    | 8KB
|32 to 64 TB    | 32KB
|64 to 128 TB   | 64KB
|128 to 256 TB  | 128KB 

![Default Cluster size](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimage.slidesharecdn.com%2Fchap2hdd2-120302094246-phpapp02%2F95%2Fchap2-hdd2-35-728.jpg%3Fcb%3D1330681666&f=1&nofb=1&ipt=c3f0e8abf01f0add4239f61c2ea054da923a5de8550526d1d22e8dd26e43d66f&ipo=images)

* NTFS supports up to 16 TB on a dynamic disk
* By tweaking the cluster sizes, NTFS can support partitions up to 16 exabytes
* NTFS supports partitions up to 16 TB by default.

### exFAT
* FAT32 does not work on drives large than 2 TB. 
* FAT32 has a max file size of 4 GB. 
* exFAT was created to break the 4-GB files-size barrier supporting files up to 16 exabyte (EB)
* exFAT literally **extends** FAT32 from 32-bit cluster entries to 64-bit cluster entries in the file table. 
* exFAT, like FAT32, does not have features like NTFS such as permissions, compression, and encryption


**Default exFAT cluster sizes in Windows**
|Volume size	|Cluster Size| 
| ------------- |:----------------:|
|7–256 MB|	4 KB	
|256 MB–32 GB|	32 KB	
|32–512 GB|	128 KB	
|512 GB–1 TB|	256 KB
|1–2 TB|	512 KB
|2–4 TB|	1 MB
|4–8 TB|	2 MB
|8-16 TB|	4 MB
|16–32 TB|	8 MB
|32–64 TB|	16 MB
|```64–512 TB```|	```32 MB```

###File System in macOS
Apple transitioned from HFS+ (Hierarchial File System Plus) to APFS (Apple File System) for a few reasons mentioned down below. MacOS can read and write to file systems such as FAT32 and exFAT, though only read NTFS.

**Reasons why Apple Transitioned to APFS:**
* HFS and HFS+ did not support nanosecond timestamps
* In HFS+ more than one process could access the filesystem at the same time which was a privacy threat
* In HFS, any given file can take up a whole allocation block size
* APFS was optimized to work with flash storage, SSD, HDD
* Uses the TRIM command to improve performance and space management
* Uses Atomic Safe Save where the computer will not save anything until the process is complete to avoid file loss or file corruption
* Future proofing: supports 64-bit inode numbers
* Cloning: instead of copying files byte by byte, clone feature enables the computer to copy the file efficiently on the same volume and not take up any more spaces. It copies the same blocks of data instead of rewriting the data.
* GPT partition scheme: in each scheme, there are a number of containers, and in each container, there are a number of APFS volumes.
* Snapshots: when you make a change to a file, APFS volumes save a pointer that points to that instance, as further changes are made, the pointer gets updated without taking up much space.
* Encrypting: supports full disk encryption from no encryption, single-key encryption, and multi-key encryption. 
* Space sharing
* Crash protection: When editing a document, the original file will not be touched, a second copy will be made. After the changes are applied and save, the original file will be deleted from the computer, and the edited file will instantly replace it. This will keep the files from being corrupted in case of a crash, and the computer won't need to write the changes twice.
* Sparse files: The computer will only allocate to a file when it needs to. So if we create a file without sufficient space if the data isn't in the file yet.



###File Systems in Linux
Most Linux distributions uses the *Fourth Extended File System (ext4)*, stably introduced in 2008. The ext4 file system supports volumes up to 1 exabyte (EB) with file sizes up to 16 TB and is backwardly compatible with ext(introduced in 1992), ext2 (introduced in 1993), and ext3 (introduced in 2001).