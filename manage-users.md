#Manage Users

###User and Groups Accounts
* What is a user account? We use to control access to resources via permissions or rights. 
* What is a group? Security group or distribution group. 
    * security group: collection of user account. using containers to assign permissions for users to simply the management process. 

### Group Types
* Local Groups
* Windows Starter and Home Edition
* Limited Standard Users - Starter/Home
* Computer Administrator - Starter/Home

### Local Groups
There is the Windows Pro, Business, Enterprise, Ultimate
* Administrators: They are like computer administrators and have complete control of the computer.
* Users: These are standard users and don't have privileges of administrators.
* Guest Users: Limited access and have the same access a user has, but after they log out, the settings are all reset. 
* Power Users

### Administrator User
* Default Administrator vs. Administrative Account
* First account with new installation
* Local vs. Domain
    * Local administrator: stored in a database individually on each computer
    * Domain: Administrator over the active directory domain 

User ```winver``` in Command Prompt to check your Windows Version. 

###Users
* Users are also known as standard users and can perform most common tasks. 
* **rights** are actions you can perform to the system **collectively**. This may be changing the system time or timezone that affects the entire computer.
* A permission is the way to control access to one specific resource and doesn't affect the system as a whole.
    * shut computer down
    * run applications (with exceptions)
    * use printers
    * install printer (with exceptions)
    * change timezone

We can use:
*  ```whoami``` to find the system name.
* ```regedit.exe``` registry editor
* ```perfmon.exe``` Performance Monitor. We can make **data collector sets (DCS)** that are counters to monitor performance. 

### Guests ###
* Limited rights
* Browse network
* Browse Internet
* Shutdown computer 
* No changes to desktop 
* Use case - kiosks

### Power Users
* Legacy group
* Backwards compatibility
* Limited administrative privileges

### System Groups
* Everyone: this group also includes Guests
* Authenticated Users
* Creator Owner
* Interactive
* Network

In order to see system logs, we have to sign in as the Administrator.

### Local User and Groups
* Local User and Groups is **not** in Home and Starter editions
* Pro, Professional, Business, Enterprise, Ultimate
* Rename and delete accounts
* Adding and removing users from groups

```Computer Management (comptmgmt.msc)--> Local Users and Groups --> Users and Groups --> right click on User --> make New User -->  ```

``` Control Panel --> User Accounts and Family Safety --> User Accounts --> Manage another account```

* Security Identifier (SID): SID is the way the OS identifies the user, and it identifies the group we are associated with.

The system will look at the access control list in there, with our ID and the Permissions of the User. However, the OS sees the Security ID. 

# Windows Management Instrumental Console 
``` C:\> wmic useraccount get name```. We will get back all the account names. However, the computer sees the SID:
``` C:\> wimic useraccount get sid```.
``` C:\> wmic useraccount get name, sid```