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


6. On Linux, **by default**, when we create new files, they are given **rw-rw-r–** permissions. The r, w, and x signify the read, write, and execute permissions, respectively.

<br />

### Command to change the owner of a file or directory

The **chown** command allows you to change the user and/or group ownership of a given file, directory, or symbolic link.

```chown USER FILE```


The command below changes the ownership of a file named file1 and directory dir1 to a new owner named linuxize:

```chown linuxize file1 dir1```
