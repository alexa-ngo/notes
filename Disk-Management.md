# Disk Management
###Disk Initialization 

When we initialize a drive, disk initialization places special information onto the drive. We are probably most familiar with seeing the status of a drive disk as Healthy, however, there are also:
* Foreign drive: when we move a dynamic disk from one computer to another computer
* Formatting: when we are formatting a drive
* Failed: Disk is damaged or corrupted, and we probably lost some data
* Online: When disk is healthy and communicating properly with the computer
* Offline: When disk is either corrupt or having communication problems

### Creating Partitions and Volumes in Disk Management
Disk Management does not enable us to specify whether we want to use a primary or extended partition when we create a volume on MBR drives. The **first** three volumes we create will be primary partitions and partitions created afterwards will be a logical drive in an extended partition. 

Tip: The command-line tool, ```diskpart```, offers more options not available in Disk Management. 

* If we have a **small partition** that is 32 GB or less, we can make the drive FAT32 or NTFS. Windows requires NTFS on any partition greater than 32 GB. When we format the partition we should use the Full Format option over the Quick Format option as the Full Format tests the blocks as part of the format process. 

### Dynamic Disks
When dynamic disks are made from basic disks in Disk Management, we no longer have primary and extended partitions. The dynamic disks are divided into volumes instead of partitions. When we move a dynamic disk from one computer to another, it shows up in Disk Management as a foreign drive. We can import a foreign drive by right-clicking the disk icon and selecting Import Foreign Disks. Lets say after using a dynamic drive, we want to convert it back to a basic drive, we can not simply revert it, or we will lose all our data. We have to back up the data before converting it back. 

###Five Types of Volumes on a Dynamic Disk
* Simple volumes: Simple volumes acts like a primary partition, however, we can not install an operating system on it. If we have only one dynamic disk in a system, we can only have one simple volume.
* Spanned volumes: Spanned volumes is when we extend the size of a simple volume to any unallocated space on a dynamic disk. We are able to use completely different dynamic disks, creating a spanned volume.  
* Striped volumes: RAID 0 array. All stripes must be the same size on each drive.
    * Stripe set: two or more drives in a group
* Mirrored volumes: RAID 1 array.
* Other levels of RAID: There is RAID 5 that uses three or more disks. Unfortunately for users using those OS, you can only make the array on a Windows Server machine. Basically, we we are going to work with more sophisticated RAID arrays, we will need the appropriate hardware and software. 

###Mounting Partitions as Folders
* mount point: A mount point is a drive that functions like a folder mounted into another drive.

____
# Storage Spaces
* storage pool: group of one or more physical drive of any size. 
* Storage Spaces: a software RAID solution in Window 8 and later that enables users to group multiple drives into a single storage pool.
* resiliency mechanism: providing one or more layers of redundancy, so we can lose a hard drive or two and not lose any data. 
    * Simple spaces: provides no resiliency, so if a drive fails, the data is lost. Simple spaces are good for temporary storage, scratch files, etc.
    * Mirror spaces: a two-way mirror requires at least two drives. A three-way mirror requires five or more drives. Mirror spaces like RAID 1 or RAID 10 gives excellent redundancy and resiliency, and robust performance. 
    * Parity spaces: similar to how a RAID 5 or RAID 6 provides redundancy. 
        * Pros: Parity spaces is more efficient than two-way mirroring. In two-way mirroring, for every 10 GB of data to be stored, 20 GB must be installed. However, with parity spaces, for every 10 GB of stored data, only 15 GB of storage needs to be installed. Partiy spaces should be used for big files that do not change a lot such as a movie collection. We can lose one drive and recover in a three-dive parity space. 
        * Cons: There is a performance overhead to manage parity spaces, which has a impact on overall performance. 

### Future Proofing
* We can future proof our storage needs.
* thin provisioning: future proofing storage needs by making a Storage Space that reports a size greater than the actual capacity installed in the computer, with the ability to later add more physical capacity up to the reported size.

### Maintaining and Troubleshooting Hard Drives:
* Blocks: one step above the physical layout of the drive, which gives a lot of flexibility in the media.
* Logical block addressing:
* Cluster: Cluster is the locations in the FAT in Windows

### Maintenance 
1. Checking for failed blocks
2. Keeping data organized for quick and easy access

#Error Checking
When individual blocks on hard drives go bad, we can use tools such as error checking to check occasionally for bad blocks on drives. When error checking finds bad blocks, the block is marked with ```0000FFF7``` in FAT/MFT so the system would not place data in the bad blocks. Error checking is a great tool to have and we should run it weekly. Many Linux distributions run ```fsck``` periodically, automatically, so we do not have to do anything at all.
```chkdsk```: check for bad blocks on drives
* Linux uses ```fsck```
* macOS uses Disk Utility
* Windows calls this Error checking

**Features of error-checking tools:**
* filenames: goes through all the filenames of the drives looking for invalid names and attempting to fix them. Blocks with no file names are called lost chains. Lost chains are blocks with no filenames associated with them. The error checking tools will erase them or save the files for our review. 
* lost parent and child: checks every parent and child folder to make sure the child folder is properly associated with its parent folder

To error check in Windows: ```Windows Explorer --> File Explorer --> right click on the drive we want to check --> Properties --> Tools tab --> click the Check or Check now button```

In macOS: ```Disk Utility --> Utilities Folder (two options): Verify Disk //or// Verify Disk and Repair Disk ```

**Defragmentation**
We should only defragment a spinning drive. If we have a **SSD**, we should **never** defragment the SSD, because it will shorten its lifetime.
* It is a good idea to defragment the drives monthly as part of the monthly maintenance process. ```Windows Explorer --> File Explorer --> right click on the drive we want to check --> Properties --> Tools tab --> Optimize Drives or Defragment now```

**Disk Cleanup**
If a hard drive becomes filled with a lot of unnecessary trash, Windows will tend to act erratically when the drive runs out of unused space. In Windows, we can use Disk Cleanup once a month to get rid of these unnecessary files.

Disk Cleanup gets rid of the four types of files:
* files in the recycle bin
* temporary internet files
* downloaded program files
* temporary files: many applications create temporary files that are supposed to be deleted when the application is closed. Unfortunately sometimes these files are not deleted and reside in a folder called "Temp".

We should run Disk Cleanup once a month so we can have plenty of space available on the hard drive. MacOS and Linux do not have a tool equivalent to Disk Cleanup, however, there is a third-party called BleachBit for Linux.

### Troubleshooting Hard Drive Implementation

Hard drives usually fail because of four reasons which are:
* installation errors
    * connectivity: does the drive show up on the UEFI or BIOs? Is it detected?
    * system setup
    * partitioning: failing to partition or making the wrong size of the partition 
    * formatting: failing to format a drive makes the drive unable to hold data
        * modern drives hide a significant number of extra bocks that they can use to replace bad blocks automatically. 
* data corruption: data can get corrupted because of power surges, accidental shutdowns, corrupted installation media, viruses, and more
    1. Run the Error checking utility
    2. Error checking will go through the blocks and mark bad blocks. It will move the data to a good block. If the same errors continue to appear after running the Error checking utility, there is a chance the drive has too many bad blocks and may need to be recycled.

    * Almost all drives takes advantage of **error correcting code** that constantly checks the drive for bad blocks. Once ECC detects a bad block, it marks the block as bad in the internal error map of the drive. Don't confused this error map with a FAT. The partitioning program creates the FAT. 
* dying hard drives
* RAID issues

