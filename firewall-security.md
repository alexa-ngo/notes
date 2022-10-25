#SOHO Network Security

###Firewalls

Firewalls can be hardware based device or it can be a software based device.

* Network-based firewalls
* Host-based firewalls

### Packet-filtering Firewall
* ACLs: Access Control List
* IP filtering
* Protocol ID/type
* Port filtering


### Host-based Firewall
* Software-based firewall
* Monitors traffic from the NIC of the host

### Firewall Settings
* Disabling ports: we want to disable ports we are not using because it is a point of entry and it is a security vector
* MAC Filtering: can be set on wired and wireless connection 
* Content Filtering/Parental Controls
* Whitelists and Blacklists: can be an application or based on a protocol, or based on URLs. 

### NAT (Network address translation)
* NAT: takes private IP addresses and translates them to public IP addresses
* NPAT, NAT overloading, PAT
    * Masks/obfuscates the internal IP address

### Port Forwarding and Port Triggering
![Port Forwarding](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fcdn-images-1.medium.com%2Fmax%2F1200%2F1*taIkKo9sDBnhAEZhxqySbQ.jpeg&f=1&nofb=1&ipt=1d5a296e8130352ae88af2cf168589ce888cd9af4c53f206a7d37e45d6750e72&ipo=images)
* Port Forwarding:
    * Takes requests from the internet for a particular protocol and sends it to a designated host
* Port Triggering:
    * Sometimes applications need more than a single port open
    * Port triggering opens the ports for an external IP address for a set period then closes it



### DMZ (Demilitarized Zone)
![DMZ](https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Faccolm.com%2Fdocumentation%2Fglobalscape-ssp%2Flib%2Fdeployment-topology.png&f=1&nofb=1&ipt=0073e0b40bb6d2ae6cd2b738b50a10eb7f8532ccc379a02e2e4f331dbc2a890e&ipo=images)
* establishes more secure communications for publicly accessible resources
* firewall is configured to expose an internal IP address (host) to the public

###UPnP (Universal Plug and Play)
* Allows for discovery and automatic configuration of network services
* Devices can request appropriate settings from a firewall
* Helpful for complex firewall setups
* Can reduce the challenges of setting up port forwarding /triggering