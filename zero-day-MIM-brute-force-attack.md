Zero-Day, Man-in-the-Middle, and Brute Force Attack

### Zero-Day

In a zero-day attack, the attacker exploits an unknown and undetected vulnerability of an application before the software companies know that a hole exists. Once the software company finds out, they will release a patch on the same day to minimize the vulnerability. The day when the loophole is discovered is called the zero-day. 

### Man-in-the-middle Attack

In a Man-In-The-Middle (MITM) attack, data packets are intercepted and possibly manipulated before the packets reaches its destination. The attacker acts like a proxy between the two parties. The attacker may deploy an *"evil router"* and capture information. This "evil router" allows the attacker to capture information and alter the messages. 

**How MITM Attack works**
1. Attack affects networks that use public key encryption.
2. User A looks for User B's public key to initiate communication.
3. Hacker intercepts the user request from User A for the public key.
4. Attacker sends their key to User A. 
5. After receiving the information from User A, the hacker re-encrypts the information and sends it to User B along with the public key of the hacker, which User B assumes to be from User A. 
6. The hacker, the middleman, continues to maintain information between both User A and User B, and continue to get information from both users. 