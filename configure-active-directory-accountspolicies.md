# Configuring Active Directory Accounts and Policies

### Active Directory Domains (this is all logical)
* Defines a logical security boundary
* Provides centralized account management
* Client/Server networking model

There are many things in an Active Directory Domain.

Active Directory Domains has: 

* Active directory database: stores all of the objects
* Policies
* Security boundary
* User and computer accounts
* Services
* Member servers
* Shared resources

SAM file: Security Accounts Manager file holds all the user account has value as a hash function. 
```This PIC --> Local Disk --> Windows --> System32 --> config --> SAM ```


``` Control Panel --> System and Security --> System ```
 The full computer name is the Computer name along with the Domain name.

 ###Active Directory Components:
 * Domain controllers (called the DC). All domain controllers have an active copy of the active directory database. If we make any edits, then the other domain controllers all sync up.
 * Active Directory database: where user and computer accounts are stored. Not everyone has the permissions to edit the active database. Every domain controller has access to the Active Directory Database.  
 * Member servers: provides a service like a file server, etc
 * User and computer accounts
 * Organizational units
 * Kerberos & SSO: Kerberos allows me to not need to log in.
 * LDAP - port 389 - Lightweight Directory Access Protocol is a directory standard that defines how we communicate with the domain controller and how we connect to a directory services database. 

 ### Domain Membership 
 * computer account objects are created in the database
 * computer and user accounts are subject to centralized domain security configuration
 * some domains can be part of the local groups
 * Fully qualified domain name (FQDN) means the Full computer name and the Domain