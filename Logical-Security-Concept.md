#Logical Security Concepts

**Learning:**
 
* Configure folder redirection
* Configure Home Folder

###Configure Folder Redirection
* A user's profile is stored on a computer that she logs on with. However, when the user logs on to another computer, a new profile is created. 
* Folder redirection allows us to redirect some of the folders from the user profile to be stored on a centralized server. After folder redirection is configured, then a user can log on any system on the network, the redirected folders will be available.


1. Create a shared folder
2. Create a GPO (Group Policy Object) to redirect the Documents folder 
```Server Manager -> Tools -> Group Policy Management```

3. Test fold redirection. We need to update the client system to receive the latest Group Policy.


### Configure Home Folder

By default, the profile of the user is stored in the Local Computer. Folder redirection allows us to redirect some of the folders from the user profile to be stored on a centralized server. After creating the folder and sharing it, we need to create a Group Policy Object to enable folder redirection. After folder redirection is configured, then a user can log on any system on the network, the redirected folders will be available for the users. When users store data in their home folder, it is easier for the administrator to backup the root folder instead of performing a backup of each individual folders from the system of the user.






