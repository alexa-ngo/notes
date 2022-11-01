# Network Share Configuration

A share is a resource shared with other users such as a folder with files, printer, hard drive that is available over the network.
A local resource is accessed when we log into the computer we are sitting at and utilizing the resource on that computer. 
* Basic Sharing
    * We share folders containing files, and not just the files by itself.
    ```Control Panel --> Network and Internet --> Network and Sharing Center```
    * UNC: Universal Naming Convention
* Advanced Sharing: gives us more sharing permissions compared to basic sharing. We can reduce the UNC path. 

**Sharing Permissions**
* Read 
* Change
* Full Control

**Administrative Shares**
* Hidden from view
* Require local Administrators groups membership
* $ sign will make any share hidden

The Share Name does not have to mark the actual path. 
* mapped drives: 

**Viewing Shares**
* Windows/File Explorer
* Mapped Drives (temporary vs. persistent)
* UNC Path (Universal Naming Convention)
* requires the appropriate permissions

**Universal Naming Convention**
* A way to identify shared resources over a network
* Shared in Unix
\\computername\sharename

* UNC format examples:
    * ```\\computername\sharename ```
    * ```\\filesrv01\marketing``` The filesrv01 is the computer name. Marketing is the sharename.
    * ```\\10.10.10.100\marketing ```

```Control Panel --> All Control Panel Items --> Sync Center ```
* We can manage offline files using the Sync Center. 
Offline Files: ```Control Panel --> All Control Panel Items --> Sync Center --> View sync partnerships --> Offline Files --> right click --> choose options```

### Print Sharing
* Printers can be mapped
* UNC Paths (Host name or IP address)
* Added or connect to through Devices and Printers
* Shared via Sharing Tab

```Control Panel --> Hardware and Sound --> Devices and Printers --> right click  ```