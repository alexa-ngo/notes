# RAID
|Raid Level  | Description   | Minimum Drives	 | Number of Functional Failures
| ------------- |:-------------:| :-------------:| :-------------:| :-------------:| 
|RAID 0|Disk Striping|2|0
|RAID 1|Disk Mirroring/Duplexing|2|1
|RAID 5|Disk Striping with Distributed Parity|3|1
|RAID 6|Disk Striping with Extra Parity|4|2
|RAID 10|Nested, Striped Mirror|4|Up to 2
|RAID 0+1|Nested, Mirrored Stripes|4|Up to 2

There are thousands of methods to set up RAID. The method chosen depends on the level of RAID we want, the operating system we use, and the amount of money want to spend.

- Serial ATA RAID controller have chips with their own processor and memory 
- almost all RAID hardware solutions provide hot-swapping
- most RAID systems have a special configuration utility in Flash ROM that we can access after CMOS but before the operating system loads. Now many motherboards have built-in RAID controllers have a CMOsS setting that enables people to turn the RAID controller on or off. 

# PATA Drive Installation
PATA drives have jumpers on the drive that must be set properly. 
- One drive: set the drive's jumpers to master or standalone
- Two drives: set one to master and the other one to slave, or set both to cable select
- if the master/slave is set incorrectly, nothing will break; it just won't work
- older motherboards have dedicated PATA ports built in, so we don't need to connect PATA cables directly to the motherboard.
- newer motherboards do not have such ports, so the PATA drives need a special add-on PATA controller expansion card.


SATA Connector: 
-
![SATA Connector](https://th.bing.com/th/id/R.8aaa905a69fff0bec9f681a7d5337bd1?rik=NfRJYV8ZUVsP9w&riu=http%3a%2f%2fwww.cs-electronics.com%2fwp-content%2fuploads%2f2014%2f12%2fSATA_Signal_Cable.jpg&ehk=gpP2g3yRXBVOeAkvn0H90oNXPGkk7mkJ9JsXoqhlA38%3d&risl=&pid=ImgRaw&r=0)

IDE Connector:
-
![IDE Connector](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2F1.bp.blogspot.com%2F-HW7r5CT2vc0%2FX2QNOZ6Hi1I%2FAAAAAAAALuE%2F9UYxbC4bs58HilJ7tHDb3wLsq4pgYkJ1wCLcBGAsYHQ%2Fw1200-h630-p-k-no-nu%2F992.png&f=1&nofb=1&ipt=53a451dfc5cf9a33bd5ad6650318123c5004b38ec5df95dd755c80e8e57bbd52&ipo=images)

____
#M.2

![enter image description here](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/M2_Edge_Connector_Keying.svg/525px-M2_Edge_Connector_Keying.svg.png)


mSATA:
-
![mSATA](https://m.media-amazon.com/images/I/818nSb4UpiL._AC_SX679_.jpg)
- the M.2 standard has been designed as a revision and improvement to the mSATA standard

____
#BIOS Support: Configuring CMOS and Installing Drivers

Every device in our PC needs BIOS support, whether it is traditional BIOS or UEFI. The same idea applies to hard drive controllers. Motherboards provides support for the SATA hard drive controllers via the system BIOS, and require configuration in CMOS for the specific hard drives that are attached. As soon as we physically attach the device the motherboard, the device is automatically detected. 

1. Configure controllers: ensure the controllers are enabled
2. Autodetection: if the controllers are enabled and the drive properly connected, the drive should appear in CMOS. The motherboards then uses a numbering system to determine how many drives are listed. 
- channels: some motherboards number each controller using the term "channels". The first boot is channel 1, the second is channel 2, and so on.

###Boot Order
Many users like to boot first from the optical drive and then from a hard drive. Booting from the optical drive first allows us to put in a bootable optical disk if there are any problems with the system. We can also set the system to boot from the hard drive and then make the necessary changes in the CMOS as well. 

**Here's a suggested boot order**
```
optical drive --> hard drive --> USB thumb drive
```

###Enabling AHCI
There are generally up to three options, modes, and host bus adapter(HBA) configuration which are:

* IDE/SATA or compatibility mode
* AHCI 
* RAID



