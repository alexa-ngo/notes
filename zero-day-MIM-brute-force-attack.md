#Cyber Attacks

[Zero-Day](#zero-day)
[Man-in-the-middle Attack](#man-in-the-middle-attack)
[Brute Force Attack](#brute-force-attack)
[Dictionary Attack](#dictionary-attack)
[Rainbow Tables](#rainbow-tables)
[Spoofing Attack](#spoofing-attack)
[Non-Compliant Systems](#non-compliant-systems)
[Zombie Systems](#zombie-systems)
[Ways to Protect Against Cyber Attacks](#ways-to-protect-against-cyber-attacks)


### Zero-Day

In a zero-day attack, the attacker exploits an unknown and undetected vulnerability of an application before the software companies are aware. Once the software company finds out, they will release a patch on the same day to minimize the vulnerability. 

A zero-day attack typically targets large organizations, departments of the government, firmware, hardware devices, IoT, and users with access to valuable business data. The best way to mitigate a zero-day attack is to fill the potential holes in security by having the latest features installed, removing outdated features, updating drivers, and fixing bugs.

The day the loophole is discovered is called the zero-day. 


### Man-in-the-middle Attack

In a Man-In-The-Middle (MITM) attack, data packets are intercepted and possibly manipulated before the packets reaches its destination. The attacker acts like a proxy between the two parties and may deploy an *"evil router"* and capture information and alter the messages.

**7 Types of MITM Attacks**
1. IP spoofing
2. DNS Spoofing
3. HTTPS spoofing
4. SSL hijacking
5. Email hijacking
6. Wi-Fi eavesdropping
7. Stealing browser cookies 

**How MITM Attack works**
1. Attack affects networks that use public key encryption.
2. User A looks for User B's public key to initiate communication.
3. Hacker intercepts the user request from User A for the public key.
4. Attacker sends their key to User A. 
5. After receiving the information from User A, the hacker re-encrypts the information and sends it to User B along with the public key of the hacker, which User B assumes to be from User A. 
6. The hacker, the middleman, continues to maintain information between both User A and User B, and continue to get information from both users. 

# Brute Force Attack
Brute force attack is when an attacker tries out all the possible combinations of the encryption key until they find one that matches. The attacker uses a special tool to crack a password and tries every possible combinations of letters, numbers, and special characters. 

# Dictionary Attack
Dictionary attacks are attempts made by attackers with the assumption that the passwords are based on dictionary words. Dictionary attacks are words from the dictionary. An attacks is not considered a dictionary attack if the passwords use a combination of letters, numbers and special characters. In a dictionary attack, the attacker enters every word from a dictionary as the input. If there is a password match, the password is exposed to the attacker. 

# Rainbow Tables
Rainbow tables are passwords stored in computers that are changed from their plain text form into an encrypted value, known as hashes. 

# Spoofing Attack
Spoofing is the act of using a false identity and gaining unauthorized access. 

Common examples of spoofing are:
* IP spoofing: IP spoofing is creating Internet Protocol (IP) packets with a false source IP address. 
* ARP spoofing: Address Resolution Protocol (ARP) spoofing is aimed to associate the MAC address of the attacker with the IP address of another host, such as a default gateway, causing the traffic meant for the IP address to be sent to the attacker instead.  
* DNS spoofing
* E-mail spoofing
* MAC spoofing

# Non-compliant Systems

A system is non-compliant if it does not follow set standards or guidelines. Systems that are poorly maintained can cause a variety of security issues such as data loss or theft. 

Organizations set security standards through:
* set of security policies (antivirus server, remote location, sensitivity of the stored data)
* specific operating system and updates
* specific set of applications

# Zombie Systems

A zombie system is an infected system connected to the Internet controlled by a hacker. The owner of the machine is unaware their machine is used for malicious attacks such as sending out spam or launching Denial-of-Service attacks. A zombie network is known as a botnet which consists of hundreds or thousands of zombie systems. Zombies are commonly used for sending spam emails and performing click frauds on Pay-Per-Click (PPC) websites. 

**Advantages of Leveraging a Zombie System**
* anonymity: if the machines performing attacks are found out, the identity of the attacker remains hidden 
* unused bandwidth: the attacker does not use their own bandwidth


# Ways to protect against cyber attacks:
* use HTTPS
* avoid phishing emails
* never connect to the public Wi-Fi routers directly
* keep security software up to date
* secure home Wi-Fi network

###Facts/Terms
* A set of security policies, specific operating system and updates, and a specific set of applications can be included in the set of security standards in an organization.
* There can be data loss on a system due to a virus attack, hard drive failure, and accidental deletion.
* A malware attack can cause application crash, system lockups, application generation unexpected output, and system slow down.
