#Denial of Service and Distributed Denial-of-Service (DDOS)

![alt text](https://sdncommunications.com/assets/images/_2000xAUTO_fit_center-center_none/DDoSAttackStructure-flat.jpg "DDoS Structure")

The Denial of Service (DoS) attack typically uses *one* computer and one internet connection to flood a targeted system or resource compared to DDoS attacks. DDoS attacks are launched from multiple connected devices which makes it harder to deflect because of the volume of devices involved. DoS attacks are launched from custom-written scripts while DDoS attacks are launched using botnets, which are large clusters of connected devices (cell phones, PCs or routers) infected with malware that allows remote control by an attacker. 

A **Distributed Denial-of Service (DDoS)** attack is a synchronized attack launched from *multiple* compromised systems on a single target. The goal is to saturate the network infrastructure with traffic to force the system to shut down. The shut down leads to the denial of service to legitimate users of the targeted system. 

If a Web server is flooded with requests in a short span of time, beyond what it can handle, the Web server will stop responding. As soon as the attacker stops sending the packets, the target system will get back to normal. However, if the target is constantly attacked, it will crash and shut down. 

### Attacker

It is easy to track and block an IP address if the attack is coming from a single computer. However, the attack might be coming from a spoofed IP address. 

###  Classification of DDoS Attacks

We can classify the DDoS attacks on the basis of:
* Network protocol stack: 
* Methodology of communication: 
* Exploits
* Attack method
* Attack rate dynamics
* Degree of automation 

##### Network Protocol Stack
Based on the OSI model, which of the two categories does the attack happen on? 
* Network/Transport Level 
* Application Level

##### Methodology of Communication
Based on how the Master Computer (System of the Attacker) communicates with the Bots. 
* Agent Handler-based attacks: attacks comprises clients, handlers, and agents. The client is one with whom the attacker communicates in the DDoS attack system. The handlers are software packages located throughout the internet. The agent software thrives in compromised systems, eventually conducting the attack at the appropriate time. 
* Internet Relay Chat (IRC)-based attacks: text-based chat system for instant messaging.
* Web-based attacks
* P2P-based attacks

##### Exploits
DDoS attacks can be classified as based on what the attacker is targeting to exploit. 

Are the attackers trying to: 
* Deplete the bandwidth
* Deplete the resource
* Exploit the protocol 
* Malformed packets

##### Attack Method
Is the DDoS attack exhausting resources or exploiting a vulnerability of a protocol in the targeted system?

The attacks are flooding attacks and logical attacks. 

* Flooding attacks: malformed packets disguised as legitimate and valid are sent to exhaust resources like bandwidth, disk space, CPU time. Flooding attacks are performed using TCP and sometimes is referred to as brute force attack.
* Logical attacks exploit the vulnerability of some protocol in the targeted system. In TCP protocol, a substantial amount of memory space is blocked immediately upon the receipt of a TCP SYN request. The attacker can flood the target system with connection requests which are never completed. The resources of the target system gets used in the process and may shut down. 

##### Attack Rate Dynamics
The attacks can come in different rates. 
* Constant rate: The constant rate can be high or low. At high rates, the multiple zombies synchronize their attacks and send large volumes of packages at the same coordinated time.
* Variable rate: The slow rate attacks are when packets are sent slowly and stealthily so the packets can not easily be detected. The variable rates uses slow and fast rates so it is harder to detect. 

##### Degree of Automation
DDoS finds vulnerable computers on the internet, exploits it, and then recruits it to become Bots or Zombies.The DDoS can be classified based on the degree of automation used in each phase. 

The classifications are:
* Manual
* Semi-Automatic
* Automatic 