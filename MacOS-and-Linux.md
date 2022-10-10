#Features and Tools of Mac OS and Linux Desktop Operating System

###Learning
* Basic Linux commands
* Best practices
* Tools

### Basic Linux commands

* chmod (change mode) : manages file and folder permissions using, read, write, and execute. 
``` 
sudo chmod 644 practicelabs.txt   # -rw-r--r--
sudo chmod 777 practicelabs.txt   # -rwx-rwx-rwx
```
* chown : change ownership of a file 
``` 
sudo chown practicelabs
practicelabs.txt
```

* cp : copies the conent from one file to another file 
```
cat alexalabs.txt
cp alexalabs.txt test.txt
cat test.txt
```
* dd : copies data. dd is used to back up the entire hard disk and hard disk partition
* ifconfig : displays network interface related parameters
* ls -l : gives more detail than 'ls'
* kill PID : terminatess a process under execution. Use ```top``` first to find the PID, then use ```kill PID```
* pwd : Print Working Directory
* passwd: assigns a password to a user account or a user to change their password
* rm : removing a file or a directory ```rm test.txt```
* sudo : Super User Do. We can add a user with ```sudo adduser practicelabs```
* vi : opens a file using the 'vi' file editor in Linux and similar OS. ```vi practice.txt``` 




#####grep
* Grep searches files based on a specified string of characters and returns the files that contains those specific characters. 
* Here are some [grep examples!](https://github.com/tldr-pages/tldr/blob/master/pages/common/grep.md)

#####mv
* renaming a file: renameme.txt linux.txt
* relocating a file: mv practice.txt Documents/

#####ps: 
process status of the current running processes. ps displays: 
* PID - Process ID
* TTY - Terminal that executed the command
* TIME - Time of a specific process
* CMD - The command that was executed 

#####yum : list all software that is currently installed, update the current software, install new software packages, and remove unneded software packages.


