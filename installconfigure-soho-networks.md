# Install Configure SOHO Networks

### Common Network Hardware
* Modem
* Router
* Switch
* Access Point

### SOHO Network Configuration
* Configuring the switch
* Browse to 192.168.0.1 or 192.168.1.1 (Class C Private address range)
* Enter default administrator name and password 

### Configuring Internet Access
* Commonly zero configuration required
* Manually defined settings are commonly wizard driven
* Obtain username/password and any other connection settings parameters from ISP
```
Access point -> modem -> RG-6 coax cable -> ISPs network
```
### Wireless Settings

Perform site survey:
* Determine required bands (2.4 GHz, 5 GHz) typically both
* Configure SSID (up to 32 characters)
* Set security implementation and encryption type
* Set pre-shared key (PSK) is the same as (password)
* Determine mode (legacy support)
* Determine appropriate channel and channel width

### IP Address Configuration

Consider static assignment for dedicated devices: 
* Printers:
* MDFs: Main Distribution Frame:  MDF is the storage space containing the hardware for the main hub of a network
* NAS:
* File servers:
* Router/ap/switch

Consider dynamic assignment of clients:
* Lower administrative burden: 

### WPS (Wi-Fi Protected Setup)
WPS is a method of setting up a secure Wi-Fi network at home with the minimum of effort.

* Easy to configure wireless network security
* Push-button security
* Advisable to disable (brute force attacks)

### Access Point Placement

Based on site survey results
* consider obstruction, reflective materials, RFI
* consider adjacent APs
* Dead zones and be mitigated with range extenders 

Dead zones are places where the antenna signals can not reach everywhere within the building. Dead zones can be mitigated with wireless repeaters. 

### Channel Selection

* Remember nonoverlapping channels
* Channel 1, 6, 11 on 2.4 GHz
* Consider using 5 GHz for more non-overlapping channels

### Radio Power Levels
* Antenna strength is measured in gain
* Increased gain results in a powerful signal
* Increasing the gain might increase interference and signal bounce 
* Decreasing signal strength might help with security

### Wireless Security Protocols
* WEP: very weak and predictable
* WPA: Wi-Fi protected access; each frame is encrypted with a unique key
* WPA2: stronger encryption 
* TKIP: every single packet or frame is encrypted with a new key
* CCMP: Cipher Block Chaining Message Authentication Code Procotol I replaced TKIP. 
* AES


|  | IV   | WEP Protocol	 | CRC
| ------------- |:-------------:| :-------------:| :-------------:| 
|WEP| Predictable|Weak| 32 Bit| 


|  | IV   | Encrypted	 | Message Integrity Code
| ------------- |:-------------:| :-------------:| :-------------:| 
|WPA|Stronger|Payload|Stronger


|   | Encrypted	 | Message Integrity Code
| ------------- |:-------------:| :-------------:| :-------------:| 
|AES-CCMP|Stronger Payload|64 Bits

### Wireless Authentication
* Open
* Personal - PSK
* Enterprise - RADIUS

### Latency and Jitter
* QoS: Quality of service. Ensure that certain types of traffic get to network resource they are required to provide the best performance.
* Some traffic is tolerant of packet loss and not in delayed communications 
    * Examples: FTP, HTTP, SMTP, POP3, SMB: tolerant of a delay in transmission but not in packet loss
* Some traffic is tolerant of delays in transmission but not packet loss (communication)
    * Examples: VoIP, HD conferencing systems, video streams: tolerant of a moderate amount of packet loss but not a delayed transmission

* Latency 
    * The time it takes for a signal to reach an endpoint
    * Video applications can support latencies of around 80 ms
    * The Internet can have peak time latency of 1000 ms
* Jitter
    * A *variation, hitch, inconsistency* in sequential packets being delivery to an endpoint
    * Often caused by congestion on the network or across the Internet

__________

### Windows Firewall
* implict deny: everything is denied unless the sources are approved
* enabling or disabling application communications
* configuring exceptions

### Windows Firewall with Advanced Security
* Windows 7/8.1
* Windows 10 - Window Defender Firewall with Advanced Security
* Configure incoming and outgoing rules
* Configure fine-grained rules
    * set incoming rule based on type, source, destination, authentication
* Configure IPSec support
* Monitoring

### Location Awareness
* Network Locations
* Home
* Work
* Public
* Domain 
* Window 8 and 10 Public vs. Private only

### Browser Configuration
* Internet Explorer
* General
* Connections Tab and Proxy Settings
* Security
* Privacy
* Programs

