# Intro to Linux


### What is a Shell?

Software that provides interface to run the commands. There is multiple.

<br />



To check shells installed

```PowerShell
cat /etc/shells 
```
<br />

To see what shell we’re using. Ps – processes

```PowerShell
ps -p $$
```   

<br />


### Root directory

Root is the first /

```PowerShell
/home/adminuser	  
```

<br />



### To download file using curl

**--outupt cat.jpg** is an output file for the download

```PowerShell
adminuser@tech241-iveta-man-app:~$ curl https://cdn.britannica.com/39/7139-050-A88818BB/Himalayan-chocolate-point.jpg --output cat.jpg
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 71944  100 71944    0     0  1756k      0 --:--:-- --:--:-- --:--:-- 1756k
```

<br />


### Renaming file

```PowerShell
adminuser@tech241-iveta-man-app:~$ mv cat.jpg cat.txt
```

<br />


### Copy file

```PowerShell
adminuser@tech241-iveta-man-app:~$ cp cat.txt cat.jpg
```

<br />


### Remove file

```PowerShell
adminuser@tech241-iveta-man-app:~$ rm cat.txt
```

<br />


### Make new dir

```PowerShell
adminuser@tech241-iveta-man-app:~$ mkdir funny-stuff
```

<br />


### Remove dir

```PowerShell
adminuser@tech241-iveta-man-app:~$ rm -r myDir
```

<br />


### Create file

```PowerShell
adminuser@tech241-iveta-man-app:~$ touch chicken-joke.txt
```

<br />


### Open file in Nano editor

```PowerShell
adminuser@tech241-iveta-man-app:~$ nano chicken-joke.txt
```

<br />


### Print file contents

```PowerShell
adminuser@tech241-iveta-man-app:~$ cat chicken-joke.txt
```

<br />



### **apt** to install packages, using **sudo** as we need to be a superuser to install

```
adminuser@tech241-iveta-man-app:~$ sudo apt install tree
```

<br />



### update

If Linux doesn’t know where the package (doesn’t have it in its sources) is well need to do more things to install:

```
adminuser@tech241-iveta-man-app:~$ sudo apt update -y
```

**y** at the end for it to say yes to all

<br />


### To get to root directory -> cd /


### If you start path with /, its starts at the root

```
adminuser@tech241-iveta-man-app:~$ cd /binroot
```

<br />

### To go to home dir: cd ~ OR cd

<br />

### Bash shell runs from **bin** folder in root

<br />

## Scripting

```
#!/bin/bash

# update

# upgrade

# install nginx

# restart nginx

# enable nginx - makes sure that when VM is restarted nginx will automatically $

sudo apt update -y

sudo apt upgrade -y

sudo apt install nginx -y

sudo service nginx restart

```

<br />

## Types of processes

Two types
1.	System processes: ps aux (see all, plus the system)
2.	User processes: ps

Every process has a process ID (PID)

<br />

### . <--- current directory

<br />

## Environmental variables


### Vieving env var

```
printenv 
```

### Vieving specific env var

```
printenv USER 
```

### Saving variable (not env)

```
MYNAME=iveta  
```


### Saving env var

```
export MYNAME=Iveta  
```


### To clear env var

```
unset MYCATSNAME 
```

Environmental variables won't be there anymore after we log out. To save it so that it stays we need to make it **persistent** 

Add env var at the end of the file. Reload after

```
nano .bashrc 
source .bashrc 
```

<br />

### Grep search file for things and highlights them

```
adminuser@tech241-iveta-man-app:~$ cat chicken-joke.txt | grep chicken
Why did the chicken cross the road?
adminuser@tech241-iveta-man-app:~$
```

<br />

## Killing processes 

Killin sleep

Makes terminal sleep for 5000 seconds. **&** puts process in the background
```
adminuser@tech241-iveta-man-app:~$ sleep 5000 & 
```

**-1** Is **hangup** signal, 3086 is process ID. Hangup is the most gentle way to end process
```
adminuser@tech241-iveta-man-app:~$ kill -1 3086 
```

**kill** on its own is **signal -15** and called **termination**. Also kills child processes.
```
adminuser@tech241-iveta-man-app:~$ kill 3086 
```

**kill -9** the HARSHEST. **Brute force** kill. Wont kill child processes, they are called zombie processes. They will be labelled as zombie in ps aux

```
adminuser@tech241-iveta-man-app:~$ kill -9 3086 
```

### File permissions

1.	Command to change file permissions: ```chmod```
2.	```chmod``` can be used only by the file **owner** or a **superuser** ( the superuser account, called **'root'**, is virtually omnipotent, with unrestricted access to all commands, files, directories, and resources. ).
3.	**“u”** for **users**, **“g”** for **group**, **“o”** for **others**, and **“ugo”** or **“a”** for **all**.  
4. **Read (r)**: Allows a user or group to view a file. 
   
    **Write (w)**: Permits the user to write or modify a file or directory.

    **Execute (x)**: A user or group with execute permissions can execute a file or view a directory. 

Examples:

chmod u=r foldername

chmod g+rwx foldername

chmod o+rw foldername

chmod o-x foldername

<br />


5. Numerical values for premissions 


- 0 = No Permission
- 1 = Execute
- 2 = Write
- 4 = Read
- 3 = -wx
- 5 = r-x
- 6 = rw-
- 7 = rwx
 
Examples:

Chmod u 6 filename

Chmod g 4 filename

Chmod o 0 filename

<br />


6. On Linux, **by default**, when we create new files, they are given **rw-rw-r–** permissions. The r, w, and x signify the read, write, and execute permissions, respectively. Execute not added by default

<br />





### Why is managing file ownership important?
All Linux files belong to an owner and a group.

### What is the command to view file ownership

To view file ownershipr ```ls -l```

### What permissions are set when a user creates a file or directory? Who does file or directory belong to?


### Why does the owner, by default, not receive X permissions when they create a file?


### Command to change the owner of a file or directory

The **chown** command allows you to change the user and/or group ownership of a given file, directory, or symbolic link.

```chown USER FILE```


The command below changes the ownership of a file named file1 and directory dir1 to a new owner named linuxize:

```chown linuxize file1 dir1```



