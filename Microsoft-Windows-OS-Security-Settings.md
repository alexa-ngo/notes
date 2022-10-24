A file server is a location to store, retrieve and process data files. File servers are designed to share disk configuration where the storage media is pooled for optimized access to network users. File servers do not perform any computational tasks such as messaging servers that manage emails or databases or how database servers process database queries. 

### User Types of the Operating System
* Administrators: Users that are administrators have complete control of the system
* Power users: Power users are more like the Users
* Users: Users are known as standard users where they do not have the capability to make any system configurations, although they are able to run applications 
* Guests: Guests have the same capability as users but have restricted capability than normal user
* Remote desktop users: Users can access the system from a remote system, and by default the administrator has remote access to the system. 

### User Account Control 
User Account Control (UAC) is a security feature in Windows that appears as a screen prompt asking for user confirmation or at times an administrator account.  


### Implement Security Best Practices to Secure a Workstation

* Local user: A local user, which is created on a Windows system, has its password information stored locally.
* Domain-based: A domain-based user account is created in Active Directory and can access various applications and network shares depending upon where the permissions have been granted.
* We can use the Active Directory Users and Computers console to create a domain-based user

###Active Directory

![Active Directory](https://docs.microsoft.com/en-us/windows-server/identity/media/using-the-organizational-domain-forest-model/c50a3c6a-b0e4-43ec-ad62-f05d05f0bbd2.gif)

**The Active Directory:**
* represents a tree-like structure 
* at the top level, there is a forest, which contains sites and domains are then part of a site
* can be multiple domains in a single forest, and each one will have its own security boundary. 
* if a policy is configured in one domain, it does not overlap in the other domain. 


###Facts/Terms
* The owner and creator of a fold or file object has full control and access of the object even when there are no user or group assigned to access the object.
* The sharing tab in te folder properties allows us to share the folder.

