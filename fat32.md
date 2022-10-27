#FAT32

When we partition a hard drive, we are partitioning a large number of blocks for the operating system to store files in a process called formatting.  

**Formatting**

Formatting is the *process* of making a partition that stores files. So what happens during formatting? First, a file system is created which allows us to store and retrieve files. Second, formatting creates a root directory in the file system to enable the partition to store files. We must format every partition to hold and store data. Every operating system has its own file system. After the format program creates the FAT, it goes through every block of the entire partition, writing and attempting to read from each block sequentially. If the operating system finds a bad block, it puts a status code in the location of the FAT of the block. The bad blocks are marked with the status code (0000FFF7) and the good blocks are marked with 00000000. 

If a hard disk has excess fragmentation, it slows down the system during hard drive reads and writes. A file may be fragmented into hundreds of pieces, forcing the reads and writes heads to travel all over the hard drive to retrieve a single file. A defragmentation program called Disk Defragmenter or Optimize Drives that can rearrange the files. Modern SSDs have a feature called trim which enables the OS to issue commands to automatically clean up and reuse deleted areas. So there is no reason to defragment ant SSD. 

1. Creates a file system: Formatting creates a file system for storing and retrieving a file. 
2. Creates a root directory: a root directory enable the partition to store folders. 


* clusters: Windows file system organize data into groups called clusters. 
* end-of-file market: Windows places the code 0000FFFF (last cluster) into the area of the cluster in the FAT to mark the last cluster. 
* full format: Full format is a format process that tests every sector to mark out the unusable blocks in the FAT. 
* quick format: Quick format creates a blank root directory in terms of Microsoft products.
* highlevel formatting: one function of high-level formatting is mapping bad blocks. 

**Operating Systems:**
* macOS: APFS and HFS+
* Linux: ext4, BTRFS, XFS, ZFS 
    *  BTRSFS: btrfs is a modern copy on write (CoW) filesystem for Linux aimed at implementing advanced features while also focusing on fault tolerance, repair and easy administration. Its main features and benefits are:
        * Snapshots which do not make the full copy of files
        * RAID - support for software-based RAID 0, RAID 1, RAID 10
        * Self-healing - checksums for data and metadata, automatic detection of silent data corruptions
    * XFS is a high-performance 64-bit journaling file system
    * ZFS is a file system with volume management capabilities.
    
    OpenZFS is a 128-bit file system while XFS is a 64-bit file system
* Windows: NTFS, FAT2, and exFAT. 

### FAT32
* base storage for hard drive stores up to 4096 bytes of data. 
* each cluster is made of one block. If a file is larger than 4096 bytes, the OS will use the needed amount of clusters to store the file, and keeps track of the stored data on the hard drive on a *structure* called the file allocation table (FAT). The FAT is a data structure that is similar to a two-column spreadsheet.
* hard drives, SSDs, and USB flash drives uses FAT32. 

**Cluster**
* each cluster is a hexadecimal number from 0000000000 to FFFFFFFF (32 bits)
* each hexadecimal character represents four binary numbers or 4 bits
* 4 billion clusters
* after saving all the clusters of a file, Windows locates the file's folders, which are stored on blocks, but they get a different set of blocks, somewhere else on the disk, and records the filename, size, date/time, and starting cluster, like this: ``` animal.txt  04-29-22 04:04p 03213ABB ```

### Process of Saving a File
1. Let's save a file called animal.txt
2. Let's use part of the FAT: from 032132ABB to 03213ACJ
3. We find the first part of the cluster at 03213AAB and we fill it.
4. We need more clusters because that is not enough space to store our file. 
5. We then use 03213ABC. 
6. Before filling 03213ABC, the value is placed in the status of 03213ABB. 
7. If we encounter a bad block marked with 0000FFF7, Windows skips it.
8. We keep going until we finish and enter the value 0000FFFF, indicating the end of the file. 
9. After saving all of the clusters, Windows locates the folder of the file, and records the filename, size, date/time, and starting cluster like this: ``` animal.txt  04-29-22 04:04p 03213ABB ```

### Process of Reading a File
1. If a program requests the file, the process is reversed.
2. Windows locates the folder containing the file to determine the starting cluster and pulls a piece of the file from each cluster until it reaches the end-of-file cluster. 
3. Windows then hands the reassembled file to the requesting application. 
4. FAT32 automatically makes two copies of the FAT. 

### Cluster Sizes in FAT32
* cluster sizes scale according to the file system.
* FAT32 offers 4KB cluster sizes up to a partition size of 2GB. 
* larger partitions require clusters with more blocks, which reduces the efficiency of that drive. 
* FAT32 is not really used for operating system partitions, but on smaller flash-media USB devices that are smaller than 32-GB. 

Take a look at the FAT 16, FAT 32, and NTFS volume sizes and clusters! Notice how as there are more features, the cluster sizes must be smaller. 
![Default Cluster size](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimage.slidesharecdn.com%2Fchap2hdd2-120302094246-phpapp02%2F95%2Fchap2-hdd2-35-728.jpg%3Fcb%3D1330681666&f=1&nofb=1&ipt=c3f0e8abf01f0add4239f61c2ea054da923a5de8550526d1d22e8dd26e43d66f&ipo=images)
![AS SSD Overall Score](https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fnews.mydrivers.com%2FImg%2F20120416%2F2012041605105205.png&f=1&nofb=1&ipt=ba2c46da8df8c7355e0e79ad1a768ece6a9f8c5eb693c972977c09928a446f23&ipo=images)

### Deleting a File
* When we delete the animal.txt file, it is not removed. Rather the the first letter of the file name is changed to a sigma symbol. It would be ```σnimal.txt```.
* Windows moves the file listing (but now the actual blocks) to a hidden directory that can be accessed through the Recycle Bin. 
* The files are not actually deleted until the Recycle Bin is empty. 
* Because the file is still intact, we can use a program such as Piriform Recuva to get the document back, or other third party tools. 
* If we want to use an undelete tool, we have to use it quickly or it will be overwritten by a new file. 

### Recover a Deleted File
* Recycle Bin: Right click the deleted file and select Restore
* Not in Recycle Bin: Microsoft does not offer any utility that can recover or restore the file and must use a third-part utility

