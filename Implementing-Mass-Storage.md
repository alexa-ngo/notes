#Implementing Mass Storage

The steps for preparing magnetic hard drive disk (HDD) or a solid state drive (SSD) are the same.
1. Partitioning: process of electronically subdividing a physical drive into one or more units called partitions.
2. Formatting: process of installing a file system onto the drive to store the files and folders.

* sectors: storage areas. A HDD has millions of sectors. Older drives had 512-byte sectors, and now they are 4,096-byte Advanced Format (AF) sectors.
* pages: 4,096-byte storage areas on SSDs 
    * block: a combined group of pages. Imagine a rectangle called a block, and within the rectangle is contains a grid where each little square is a page.

The operating system and the CPU never talks to these internal structures. Instead, there is a controller on the HDD or SSD that uses the logical block addressing (LBA). The operating system or the CPU will request for the LBA number. The LBA chunks are also called blocks. The operating system interacts with mass storage in blocks. 

How LBA works: ``` CPU asks for LBA number 23,432,342,676! --> message goes to the Chipset --> message goes to the Drive connector ```

### Three Partitioning Methods

Windows supports three partitioning methods called the master boot record (MBR), Windows' proprietary dynamic partition scheme, and GPT. A system may have a combination of all three drives. 

* master boot record (MBR) partitioning scheme. Microsoft calls a hard drive that uses MBR a basic disk.
* Windows' proprietary dynamic storage partitioning scheme. Microsoft calls a drive that uses the dynamic storage partitioning scheme a dynamic disk.
* GUID partition table (GPT). Microsoft calls a hard drive that uses GPT a basic disk. The GPT is a new disk architectures that expands on the older MBR. 

### Master Boot Record

The master boot record informs the system about the installed operating systems. When the system is booting up, the BIOS looks for the first sector of the hard drive for instructions. Without this bit of code, the OS will never load. The master boot drive also contains the partitions table, which describes the number of partitions and size of partitions on the disk. The MBR can only support up to **4 partitions**. 

How the master boot record works: 

```
In Sector 0:
    1. The MBR looks for a partition with an operating system.
    2. The partition table tells the MBR where to look. 
    3. The MBR locates the appropriate partition, the partition boot sector loads the OS on that partition. 
    4. The partition boot sector stores information important to its partition, such as the location of the OS boot files.    
```
The MBR partition tables support two types of partitions:
* primary partition
* extended partition

### Primary Partitions and Multiple Operating Systems
Primary partitions are usually assigned drive letters that we see in Windows Explorer/File Explorer after they are formatted. The primary partitions may be called C:, D:, through Z:. Every primary partition on a single drive has a special setting stored in the partition table called active that determines the active partition. 

**During the Boot-Up Process**
```
1. BIOS/POST reads the MBR to find the active partition.
2. Boots the OS on that partition. 
Only one partition can be active at a time because only one operating system can be running at a time.
```

Personally, I have two operating systems on my machine. One Windows and one Linux(Ubuntu). I use GRUB (Grand Unified Bootloader), a free Linux-based boot manger, to control multiboot setups. 

###Extended Partitions
* There is a four partition limit. If a MBR disk is using only primary partitions, it would be limited to only four drive letters.
* An extended partition overcomes the limit of four-partitions by using an extended partition which contains multiple logical drives, each of which can get a drive letter.
* Extended partitions can not boot an operating system from it. 

### Dynamic Partition

Features of a dynamic disk:
1. Create as many volumes. The number of volumes is not limited to just four partitions.
2. Ability to create new drive structures using software not possible in MBR drives. It is possible to implement RAID, span volumes over multiple drives, and extend volumes on one or more drives.

Only lower-end versions of Windows 7 do not support dynamic disks. Every version and edition after that will support dynamic disks.

* simple volumes: Simple volumes work like primary partitions.
* spanned volumes: unallocated space on multiple drives used to make a single volume.
* striped volumes: Raid 0 volumes. Raid 0 takes unallocated spaces on two separate hard drives and stripe them. If either drive goes down, all the data is gone.
* mirror volumes: Raid 1 volumes.
* RAID 5 volumes: Raid 5 requires three or more dynamic disks with equal-sized unallocated spaces. 

### GUID Partition Table

GUID, globally unique identifier, is a unique reference number for an object or process that almost has no change of it being a duplication. 

GUID Partition Table is an improvement to MBR:

|               |  MBR          | GPT 	         | 
| ------------- |:-------------:| :-------------:|
|Partition Limit| 4             |128             | 
|Max Size Limit | 2.2 TB        |No Restrictions (zettabytes)
|Arrangement    | Sectors       |LBA             |
|Booting        | master boot record and partition table| GPT header and partition entry array |

* GPT drive can have almost unlimited number of primary partitions. Microsoft has limited Windows to 128 partitions. 


* hidden partition: Hidden partition, also known as a factory recovery partition, is a primary partition hidden from the operating system. Only special BIOS tools may access a hidden partition. Sometimes PC makers hide a backup copy of an installed OS that we can use to restore the system with. 
* swap partition: Swap partitions are found in Linux and UNIX systems, where its jobs is to act like RAM when the system needs more RAM than installed. Windows has a similar function with a page file that uses a file instead of a partition. 

________
#When to Partition

We would need partitioning when:
* install an OS on a new system
* adding drives to an existing system

For Windows, through the days of DOS and early Windows we use `FDISK` to partition drives. Now we use Disk Management and the CLI called `diskpart`. Linux uses `GParted` as a partitioning tool. 