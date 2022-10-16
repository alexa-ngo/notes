#Network Configuration Network Services

##FTP
* FTP is not encrypted.
* get file
* push file
* FTP uses Port 20 and port 21
* www is not the same as the internet. The internet is much larger. 
  

## SMB (Server Message Block)
* SMB2 is the current implementation. 
* If SMB is bundled with TCP/IP and NetBIOS, it uses ports 137, 138, and 139. 

## Network Host Services
* Authentication Server: proves identity. Authentication, authorization, and accounting.
* RADIUS: how we verify identities
* Kerberos protocol

## LDAP
* Lightweight Domain Access Protocol (LDAP): communicating with a directory services server.

* NetBIOS: software used very early on in Windows network for discovery of computers, resources and session establishment
* NetBT: as TCP/IP became the standard for LANs NetBIOS was reengineered. 
* NetBIOS over TCP/IP
* **Name service - UDP port 137**
* **Datagram transmission service - UDP port 138**
* **Session services - TCP port 139**

## Inventory Management Servers
* Inventory Management: managing the assets of the devices running on the network. Example: tracking 10,000 computers at the company.

### SNMP
* Framework for management and monitoring of network devices
* Agent: process software running on the switch that communicates with the monitoring software
* MIB: holds the stats and the activity of the device
* Trap: operation where a device informs the management system of a noticeable event
* Port = queries - UDP port 161
* Port = trap communications - UPD port 162

## Endpoint Management Server
* Endpoint Management Server
* syslog
* Client/Server software that allows for the capturing logs from different devicess
* Unix/Linux logging system
* Runs locally but can be sent to a syslos server for centralized management
* Example devices - routers switches, servers, workstations

## Legacy and Embedded Systems
* Embedded Systems: computer designed to do a specific function. When vendors do not support the system, it can be a security concern. These systems can be highly prioritary. 
* Legacy Systems: system no longer supported by the vendor where patch management and maintenance can be challenging which is a security risk to the organization

## Internet Security Appliances and Software
* IDS: intrusion detection system, sends an alert of the intrusion
* IPS: intrution prevention system, sends an alert of the intrusion, and actively implements **counter measures** The IPS sits closer to the internet compared to IDS. 
* UTM:Unified Threat Management can be installed inline with the network. Can install the application as a network sensor. Taking firewall, IDS, IPS, and blending it to be in one location. 

### Proxy server:
* Mostly implemented by companies 
* Forward proxy: hides the identity of the Clients --> DMZ (Demilitarized Zone) --> Internet
* Reverses proxy: hides the identity of the FTP server --> DMZ --> LAN and FTP 
* depends on the **direction** of what is being proxy



















