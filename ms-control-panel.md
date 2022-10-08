# Using Microsoft Windows Control Panel's User Related Utilities

**Learning:**

* Configuring Firewall Rules using Windows Firewall
* Power Options
* HomeGroup
* Network and Sharing Center
* Device Manager

**Configuring Firewall Rules using Windows Firewall**

The firewall analyzes the packets coming to the computer or network and sees if the firewall specified conditions are met. The firewall will allow or deny access to the computer or network based on the rules. 


**Verify that the network connection is enabled.**

* If two computers are connected to each other over the network they have a live connection to communicate with each other. We can verify that there is a live connection by pinging one computer from the other by using `ping`. 


**Create a Simple Windows Firewall Rule**

* We can specify whether a firewall rule applies to LAN/WAN/remote access/all of these modes of operation of the computer. 
    1. Create a rule to block incoming packets: 
    `Windows Firewall → Allow a program or feature through Windows Firewall → clear the boxes under File and Printer Sharing`

**Power Options**
* Hibernate option: shuts the machine, but open applications are stored in memory.
* Sleep option: puts the machine in a low power-consuming mode. 
* Standby mode: when a machine has been idle for a period of time.

**Working with HomeGroup**
* HomeGroup is a group of personal computers on a home network that can share resources like files and printers. These resources may not all be available on a local machine. It could be available with other machines on the same network. 

**Using the Network and Sharing Center**
* We can use the Network and Sharing Center to share the local machine's media to the other machines on the network. 

**Using Device Manager**
* The Devlice Manager contains the list of all the internal and external peripheral devices of the computer system. It has the human interface devices, processors, disk drives, network adapters, and many other hardware devices. 

**Facts:**
* The private network, domain network, and public network are available in Windows Firewall in Windows 10.
* The driver date, driver version, digital signer, and driver provider is available in Device Manger for a specific device driver.
* Windows 10 has hibernate, standby, and sleep as a power option.
* Programs and features allows us to remove an application in Windows 10.
* The device manager provides us with a list of attached internal and external peripheral devices and installed drivers. 

