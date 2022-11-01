# Disk Management
###Disk Initialization 

When we initialize a drive, disk initialization places special information onto the drive. We are probably most familiar with seeing the status of a drive disk as Healthy, however, there are also:
* Foreign drive: when we move a dynamic disk from one computer to another computer
* Formatting: when we are formatting a drive
* Failed: Disk is damaged or corrupted, and we probably lost some data
* Online: When disk is healthy and communicating properly with the computer
* Offline: When disk is either corrupt or having communication problems

### Creating Partitions and Volumes in Disk Management
Disk Management does not enable us to specify we want to use a primary or extended partition when we create a volume on MBR drives. The **first** three volumes we create will be primary partitions and partitions created afterwards will be a logical drive in an extended partition. The command-line tool, ```diskpart```, offers more options not available in Disk Management. If we have a **small partition** that is 32 GB or less, we can make the drive FAT32 or NTFS. Windows requires NTFS on any partition greater than 32 GB. When we format the partition choose the Full Format option over the Quick Format option because the Quick Format tests the blocks as part of the format process. 