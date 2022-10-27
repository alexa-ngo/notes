# Configure Remote Access

### Remote Desktop
* Establishes remote connections: The location machine will open the port to establish connection. The computer requesting the connection does not have to do much. 
* Taking control over the desktop
* RDP 3389 (Remote Desktop Protocol)
* Uses NLA (helps to mitigate DoS attacks)
    * Network Level Authentication is a feature of Remote Desktop Services or Remote Desktop Connection that requires the connecting user to authenticate themselves before a session is established with the server
* Not available in Home editions
* Limited to a single person
* The remote desktop is **disabled by default**

### Remote Assistance
* Allows for the remote viewing and sharing the desktop
* Great for help desk and support
* Uses ephemeral ports
* Difficult to set up firewall support
* Available for the home edition
* the connection is made automatically by turning it on
* ephemeral port: An ephemeral port is a communications endpoint ( port) of a transport layer protocol of the Internet protocol suite that is used for only a short period of time for the duration of a communication session. The range are high level dynamic ports ranging from 49k - 65k port number.
* The remote assistance is **enabled by default**
* hard to set up a firewall since these ports are *dynamic* ports

Here is how Remote Desktop works: ``` invitation file --> sent to helper --> click --> IT connects to the machine ```

### Remote Credential Guard
* users credentials remain on the client
* can run in restricted mode(RDP Restricted Admin or RDPRA); user logs on as local administrator (cannot present domain user credential)
* protects from a **Pass-the-hash attack**
* client/remote PC Windows 10, version 1607, Windows Server 2016
* RDPRA - remote PC must be a patch Windows 7 or Windows Server 2008 R2

Pass-the-hash attack: when an attack steals the users hashed password value and uses it to trick the authentication system.

### Remote Assistance Process
* Generated a Remote Assistance request
* Request format: file, email, Easy Connect
* Same encryption techniques as RDP
* Helper must open the invitation request file
* Helpee has to authorize the connection request and has the ability to stop sharing
* Helper can request control over the desktop 
* Chat is available

* Easy Connect - allows for a password only (not invitation file)
* Easy Connect has been superceded by Quick Assist in Windows 10

**How to Request someone to help using Remote Assistance:**

``` Windows Remote Assistance --> Invite someone you trust to help you --> Save the invitation to the Desktop or file server to make the remote assistance connection --> copy the password --> connect to the file share --> copy the file to the helpee desktop --> click on the icon --> Remote Assistance will pop up --> Enter the temporary password --> the helpee needs to click 'yes' ```

**End the Remote Assistance**
