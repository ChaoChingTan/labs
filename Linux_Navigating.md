# Navigating the Filesystem

## Objectives
Understand the basic commands when working with file and directories in Linux.  

## Working with Directories

Commands for working with directories include:

* pwd - print working directory
* cd - change directory
* ls - list directory contents
* mkdir - make directories
* rmdir - remove directories

### pwd

**pwd** prints the name of current/working directory.  When logging into a Linux system, the user will initially be working in their home directory. 

```bash
[student@ip-172-31-88-88 ~]$pwd
/home/student
[student@ip-172-31-88-88 ~]$
```

### cd

**cd** changes the current directory to the one specified.  If no arguments are provided, cd changes the current directory to the user's home directory.

```bash
[student@ip-172-31-88-88 ~]$pwd
/home/student
[student@ip-172-31-88-88 ~]$cd /
[student@ip-172-31-88-88 /]$pwd
/
[student@ip-172-31-88-88 /]$cd /home
[student@ip-172-31-88-88 home]$pwd
/home
[student@ip-172-31-88-88 home]$cd 
[student@ip-172-31-88-88 ~]$pwd
/home/student
[student@ip-172-31-88-88 ~]$
```

### ls

**ls** lists directory contents.  Options can be provided, for example:
- -a
  - do not ignore entries starting with .
- -l  
  - use a long listing format

```bash
[student@ip-172-31-88-88 ~]$ls
[student@ip-172-31-88-88 ~]$ls -l
total 0
[student@ip-172-31-88-88 ~]$ls -a
.  ..  .bash_history  .bash_logout  .bash_profile  .bashrc  .cache  .lesshst
[student@ip-172-31-88-88 ~]$ls -la
total 20
drwx------. 3 student student 113 Oct  4 09:02 .
drwxr-xr-x. 5 root    root     50 Oct  4 04:54 ..
-rw-------. 1 student student 463 Oct  4 08:03 .bash_history
-rw-r--r--. 1 student student  18 Nov 24  2022 .bash_logout
-rw-r--r--. 1 student student 141 Nov 24  2022 .bash_profile
-rw-r--r--. 1 student student 492 Nov 24  2022 .bashrc
drwxr-xr-x. 3 student student  18 Oct  4 07:55 .cache
-rw-------. 1 student student  32 Oct  4 09:02 .lesshst
[student@ip-172-31-88-88 ~]$
```

Refer to the man page for more options and details. 

### mkdir

**mkdir** make directories.    

```bash
[student@ip-172-31-88-88 ~]$pwd
/home/student
[student@ip-172-31-88-88 ~]$ls -ld
drwx------. 3 student student 113 Oct  4 09:09 .
[student@ip-172-31-88-88 ~]$mkdir testdir
[student@ip-172-31-88-88 ~]$ls -la
total 20
drwx------. 4 student student 128 Oct  4 09:10 .
drwxr-xr-x. 5 root    root     50 Oct  4 04:54 ..
-rw-------. 1 student student 463 Oct  4 08:03 .bash_history
-rw-r--r--. 1 student student  18 Nov 24  2022 .bash_logout
-rw-r--r--. 1 student student 141 Nov 24  2022 .bash_profile
-rw-r--r--. 1 student student 492 Nov 24  2022 .bashrc
drwxr-xr-x. 3 student student  18 Oct  4 07:55 .cache
-rw-------. 1 student student  32 Oct  4 09:09 .lesshst
drwxr-xr-x. 2 student student   6 Oct  4 09:10 testdir
```

User will need to have write permissions to the current working directory to make directories.  For example, the **mkdir** command in the example below fails due to insufficient permissions.  

```bash
[student@ip-172-31-88-88 ~]$cd /
[student@ip-172-31-88-88 /]$ls -ld
dr-xr-xr-x. 19 root root 246 Oct  3 07:29 .
[student@ip-172-31-88-88 /]$mkdir testdir
mkdir: cannot create directory ‘testdir’: Permission denied
[student@ip-172-31-88-88 /]$
```

## Working with Files

Commands for working with files include:

* file - determine file type
* touch - change file timestamps
* rm - remove files or directories (-rf option to remove non-empty directories)
* cp - copy files and directories
* mv - move (rename) files

### file

**file** is used to determine file type of a file.  For example, it can be used to ensure that the file is in plain text and not binary before viewing the file contents.  

```bash
[student@ip-172-31-88-88 /]$file /etc/passwd
/etc/passwd: ASCII text
[student@ip-172-31-88-88 /]$which file
/usr/bin/file
[student@ip-172-31-88-88 /]$file /usr/bin/file
/usr/bin/file: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=cb7dc2bf0327dcb662cea949395bf9056ec802fe, for GNU/Linux 3.2.0, stripped
[student@ip-172-31-88-88 /]$
```

### touch

**touch** is used to change file timestamps of the file specified.  If the file does not exist, it will create an empty file.

```bash
[student@ip-172-31-88-88 ~]$pwd
/home/student
[student@ip-172-31-88-88 ~]$ls -l 
total 0
drwxr-xr-x. 2 student student 6 Oct  4 09:10 testdir
[student@ip-172-31-88-88 ~]$touch file
[student@ip-172-31-88-88 ~]$ls -l 
total 0
-rw-r--r--. 1 student student 0 Oct  4 09:49 file
drwxr-xr-x. 2 student student 6 Oct  4 09:10 testdir
[student@ip-172-31-88-88 ~]$
```

### rm

**rm** remove files or directories (-rf option to remove non-empty directories)

```bash
[student@ip-172-31-88-88 ~]$ls -l
total 0
-rw-r--r--. 1 student student 0 Oct  4 09:49 file
drwxr-xr-x. 2 student student 6 Oct  4 09:10 testdir
[student@ip-172-31-88-88 ~]$rm file
[student@ip-172-31-88-88 ~]$ls -l
total 0
drwxr-xr-x. 2 student student 6 Oct  4 09:10 testdir
[student@ip-172-31-88-88 ~]$rm testdir
rm: cannot remove 'testdir': Is a directory
[student@ip-172-31-88-88 ~]$rm -rf testdir
[student@ip-172-31-88-88 ~]$ls -l
total 0
[student@ip-172-31-88-88 ~]$
```

### cp 

**cp** is used to copy files and directories.

```bash
[student@ip-172-31-88-88 ~]$ ls -l
total 0
[student@ip-172-31-88-88 ~]$ touch testfile
[student@ip-172-31-88-88 ~]$ ls -l
total 0
-rw-r--r--. 1 student student 0 Oct  4 09:57 testfile
[student@ip-172-31-88-88 ~]$ cp testfile copy_of_testfile
[student@ip-172-31-88-88 ~]$ ls -l
total 0
-rw-r--r--. 1 student student 0 Oct  4 09:57 copy_of_testfile
-rw-r--r--. 1 student student 0 Oct  4 09:57 testfile
[student@ip-172-31-88-88 ~]$ 
```

### mv

**mv** is used to move (rename) files.

To rename a file from *copy_of_testfile* to *testfile2*:

```bash
[student@ip-172-31-88-88 ~]$ ls -l
total 0
-rw-r--r--. 1 student student 0 Oct  4 09:57 copy_of_testfile
-rw-r--r--. 1 student student 0 Oct  4 09:57 testfile
[student@ip-172-31-88-88 ~]$ mv copy_of_testfile testfile2
[student@ip-172-31-88-88 ~]$ ls -l
total 0
-rw-r--r--. 1 student student 0 Oct  4 09:57 testfile
-rw-r--r--. 1 student student 0 Oct  4 09:57 testfile2
```

To move *testfile2* from current directory to */tmp*:

```bash
[student@ip-172-31-88-88 ~]$ mv testfile2 /tmp
[student@ip-172-31-88-88 ~]$ ls -l
total 0
-rw-r--r--. 1 student student 0 Oct  4 09:57 testfile
[student@ip-172-31-88-88 ~]$ ls -l /tmp/testfile2 
-rw-r--r--. 1 student student 0 Oct  4 09:57 /tmp/testfile2
[student@ip-172-31-88-88 ~]$ 
```


## Working with File Contents

Commands for working with file contents include:

* head - output the first part of files
* tail - output the last part of files
* cat - concatenate files and print on the standard output
* more - file perusal filter for crt viewing
* less - opposite of more (but does more or less the same thing!)

### head

**head** outputs the first part of files. By default it shows the first 10 lines of the file:

```bash
[student@ip-172-31-88-88 /]$head /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
```
The default behaviour can be modified by supplying options.  To show the first 5 lines, use the '-5' option. 

```bash
[student@ip-172-31-88-88 /]$head -5 /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
[student@ip-172-31-88-88 /]$
```
Refer to the man page for more options and details. 


### tail

**tail** outputs the last part of files. By default it shows the last 10 lines of the file:

```bash
[student@ip-172-31-88-88 /]$tail /etc/passwd
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:998:996:User for polkitd:/:/sbin/nologin
tss:x:59:59:Account used for TPM access:/dev/null:/sbin/nologin
sssd:x:997:994:User for sssd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/usr/share/empty.sshd:/sbin/nologin
chrony:x:996:993:chrony system user:/var/lib/chrony:/sbin/nologin
systemd-oom:x:991:991:systemd Userspace OOM Killer:/:/usr/sbin/nologin
admin:x:1000:1000:user:/home/admin:/bin/bash
student:x:1001:1001::/home/student:/bin/bash
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
[student@ip-172-31-88-88 /]$
```
The default behaviour can be modified by supplying options.  To show the last 2 lines, use the '-2' option.  Refer to the man page for more options and details. 

```bash
[student@ip-172-31-88-88 /]$tail -2 /etc/passwd
student:x:1001:1001::/home/student:/bin/bash
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
[student@ip-172-31-88-88 /]$
```

### cat, more, less

**cat**, **more** and **less** are utilities for using files.  **cat** dumps out the entire content of the file at one go:

```bash
[student@ip-172-31-88-88 /]$cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
.
.
<output truncated>
.
.
student:x:1001:1001::/home/student:/bin/bash
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
[student@ip-172-31-88-88 /]$
```

The **more** command is a command-line pager, used to display the contents of a text file or command output one screen at a time. It allows users to navigate through the text using keyboard commands, such as the spacebar to advance to the next page, the Enter key to move line by line, and the 'q' key to exit. more is commonly used when viewing large text files, providing a simple and straightforward way to browse and read content without overwhelming the terminal with information.

**less** works similar to **more** but includes additional features.  Refer to the manual page for more details.  

## References
* [Linux Fundamentals, Paul Cobbaut](https://linux-training.be/linuxfun.pdf)
  * Chapter 8 - Working with Directories
  * Chapter 9 - Working with Files
  * Chapter 10 - Working with File Contents
