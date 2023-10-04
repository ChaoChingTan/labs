# Software Installation

## Objectives
- Package management on Linux systems
- Installing software
- Removing software

## Introduction
Software is typically installed via packages on Linux systems.  To administer a Linux system, you will need to know how to add, remove and update software.  

## Package Management

**Source packages** contain the original human-readable source code of a software application.

**Binary packages** contain pre-compiled executable files, libraries, and other necessary files needed to run the software on a specific system architecture.

### Low Level Tools

Low level package management tools works directly with the package files without resolving dependencies:  

* dpkg - for Debian based systems
* rpm - for Redhat based systems

### High Level Tools

High level package management tools automatically resolves dependencies, fetches packages from repositories, and handles upgrades.

The high level tools utilize the corresponding low level tools in the backend: 

* yum (Yellowdog Updater Modified) - used in Red Hat-based systems, including RHEL, Fedora, and CentOS
* dnf (Dandified YUM) - successor to yum
* apt-get - used in Debian-based systems, including Debian and Ubuntu


### Software Installation on Redhat based systems

To install packages on Redhat based systems, use the `dnf install` command.  To install the latest version of packages, use the `dnf update` command.

Note that superuser privilege is required for software installation.

For more information on the `dnf` command, check the friendly manual pages:

```bash
man dnf
```

### Example - Software Installation / Removal
The httpd package contains the Apache httpd server.  To find out more information about this package, run the command `dnf info httpd`:

```bash
[student@ip-172-31-88-88 ~]$sudo dnf info httpd
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:22:13 ago on Wed 04 Oct 2023 07:50:57 AM UTC.
Installed Packages
Name         : httpd
Version      : 2.4.53
Release      : 11.el9_2.5
Architecture : x86_64
Size         : 59 k
Source       : httpd-2.4.53-11.el9_2.5.src.rpm
Repository   : @System
From repo    : rhel-9-appstream-rhui-rpms
Summary      : Apache HTTP Server
URL          : https://httpd.apache.org/
License      : ASL 2.0
Description  : The Apache HTTP Server is a powerful, efficient, and extensible
             : web server.

[student@ip-172-31-88-88 ~]$
```

Install httpd using `dnf install` command

```bash
[student@ip-172-31-88-88 ~]$dnf install httpd
Not root, Subscription Management repositories not updated
Error: This command has to be run with superuser privileges (under the root user on most systems).
[student@ip-172-31-88-88 ~]$sudo dnf install httpd
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:05:13 ago on Wed 04 Oct 2023 07:50:57 AM UTC.
Dependencies resolved.
================================================================================
 Package            Arch   Version             Repository                  Size
================================================================================
Installing:
 httpd              x86_64 2.4.53-11.el9_2.5   rhel-9-appstream-rhui-rpms  53 k
Installing dependencies:
 apr                x86_64 1.7.0-11.el9        rhel-9-appstream-rhui-rpms 127 k
 apr-util           x86_64 1.6.1-20.el9_2.1    rhel-9-appstream-rhui-rpms  97 k
 apr-util-bdb       x86_64 1.6.1-20.el9_2.1    rhel-9-appstream-rhui-rpms  14 k
 httpd-core         x86_64 2.4.53-11.el9_2.5   rhel-9-appstream-rhui-rpms 1.5 M
 httpd-filesystem   noarch 2.4.53-11.el9_2.5   rhel-9-appstream-rhui-rpms  17 k
 httpd-tools        x86_64 2.4.53-11.el9_2.5   rhel-9-appstream-rhui-rpms  87 k
 mailcap            noarch 2.1.49-5.el9        rhel-9-baseos-rhui-rpms     35 k
 redhat-logos-httpd noarch 90.4-1.el9          rhel-9-appstream-rhui-rpms  18 k
Installing weak dependencies:
 apr-util-openssl   x86_64 1.6.1-20.el9_2.1    rhel-9-appstream-rhui-rpms  16 k
 mod_http2          x86_64 1.15.19-4.el9_2.4   rhel-9-appstream-rhui-rpms 153 k
 mod_lua            x86_64 2.4.53-11.el9_2.5   rhel-9-appstream-rhui-rpms  63 k

Transaction Summary
================================================================================
Install  12 Packages

Total download size: 2.2 M
Installed size: 6.0 M
Is this ok [y/N]: y
Downloading Packages:
(1/12): apr-1.7.0-11.el9.x86_64.rpm             1.9 MB/s | 127 kB     00:00    
(2/12): redhat-logos-httpd-90.4-1.el9.noarch.rp 273 kB/s |  18 kB     00:00    
(3/12): mod_http2-1.15.19-4.el9_2.4.x86_64.rpm  2.1 MB/s | 153 kB     00:00    
(4/12): mod_lua-2.4.53-11.el9_2.5.x86_64.rpm    4.8 MB/s |  63 kB     00:00    
(5/12): httpd-2.4.53-11.el9_2.5.x86_64.rpm      3.4 MB/s |  53 kB     00:00    
(6/12): httpd-tools-2.4.53-11.el9_2.5.x86_64.rp 5.8 MB/s |  87 kB     00:00    
(7/12): apr-util-1.6.1-20.el9_2.1.x86_64.rpm    5.8 MB/s |  97 kB     00:00    
(8/12): apr-util-bdb-1.6.1-20.el9_2.1.x86_64.rp 1.2 MB/s |  14 kB     00:00    
(9/12): httpd-core-2.4.53-11.el9_2.5.x86_64.rpm  32 MB/s | 1.5 MB     00:00    
(10/12): httpd-filesystem-2.4.53-11.el9_2.5.noa 853 kB/s |  17 kB     00:00    
(11/12): apr-util-openssl-1.6.1-20.el9_2.1.x86_ 980 kB/s |  16 kB     00:00    
(12/12): mailcap-2.1.49-5.el9.noarch.rpm        2.5 MB/s |  35 kB     00:00    
--------------------------------------------------------------------------------
Total                                            11 MB/s | 2.2 MB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Installing       : apr-1.7.0-11.el9.x86_64                               1/12 
  Installing       : apr-util-bdb-1.6.1-20.el9_2.1.x86_64                  2/12 
  Installing       : apr-util-openssl-1.6.1-20.el9_2.1.x86_64              3/12 
  Installing       : apr-util-1.6.1-20.el9_2.1.x86_64                      4/12 
  Installing       : httpd-tools-2.4.53-11.el9_2.5.x86_64                  5/12 
  Installing       : mailcap-2.1.49-5.el9.noarch                           6/12 
  Running scriptlet: httpd-filesystem-2.4.53-11.el9_2.5.noarch             7/12 
  Installing       : httpd-filesystem-2.4.53-11.el9_2.5.noarch             7/12 
  Installing       : httpd-core-2.4.53-11.el9_2.5.x86_64                   8/12 
  Installing       : mod_http2-1.15.19-4.el9_2.4.x86_64                    9/12 
  Installing       : mod_lua-2.4.53-11.el9_2.5.x86_64                     10/12 
  Installing       : redhat-logos-httpd-90.4-1.el9.noarch                 11/12 
  Installing       : httpd-2.4.53-11.el9_2.5.x86_64                       12/12 
  Running scriptlet: httpd-2.4.53-11.el9_2.5.x86_64                       12/12 
  Verifying        : apr-1.7.0-11.el9.x86_64                               1/12 
  Verifying        : redhat-logos-httpd-90.4-1.el9.noarch                  2/12 
  Verifying        : mod_http2-1.15.19-4.el9_2.4.x86_64                    3/12 
  Verifying        : mod_lua-2.4.53-11.el9_2.5.x86_64                      4/12 
  Verifying        : httpd-2.4.53-11.el9_2.5.x86_64                        5/12 
  Verifying        : httpd-core-2.4.53-11.el9_2.5.x86_64                   6/12 
  Verifying        : httpd-tools-2.4.53-11.el9_2.5.x86_64                  7/12 
  Verifying        : apr-util-1.6.1-20.el9_2.1.x86_64                      8/12 
  Verifying        : apr-util-bdb-1.6.1-20.el9_2.1.x86_64                  9/12 
  Verifying        : httpd-filesystem-2.4.53-11.el9_2.5.noarch            10/12 
  Verifying        : apr-util-openssl-1.6.1-20.el9_2.1.x86_64             11/12 
  Verifying        : mailcap-2.1.49-5.el9.noarch                          12/12 
Installed products updated.

Installed:
  apr-1.7.0-11.el9.x86_64                                                       
  apr-util-1.6.1-20.el9_2.1.x86_64                                              
  apr-util-bdb-1.6.1-20.el9_2.1.x86_64                                          
  apr-util-openssl-1.6.1-20.el9_2.1.x86_64                                      
  httpd-2.4.53-11.el9_2.5.x86_64                                                
  httpd-core-2.4.53-11.el9_2.5.x86_64                                           
  httpd-filesystem-2.4.53-11.el9_2.5.noarch                                     
  httpd-tools-2.4.53-11.el9_2.5.x86_64                                          
  mailcap-2.1.49-5.el9.noarch                                                   
  mod_http2-1.15.19-4.el9_2.4.x86_64                                            
  mod_lua-2.4.53-11.el9_2.5.x86_64                                              
  redhat-logos-httpd-90.4-1.el9.noarch                                          

Complete!
[student@ip-172-31-88-88 ~]$
```

To remove packages on Redhat based systems, use the `dnf remove` command as root. 

```bash
[student@ip-172-31-88-88 ~]$sudo dnf remove httpd
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Dependencies resolved.
================================================================================
 Package            Arch   Version            Repository                   Size
================================================================================
Removing:
 httpd              x86_64 2.4.53-11.el9_2.5  @rhel-9-appstream-rhui-rpms  59 k
Removing unused dependencies:
 apr                x86_64 1.7.0-11.el9       @rhel-9-appstream-rhui-rpms 289 k
 apr-util           x86_64 1.6.1-20.el9_2.1   @rhel-9-appstream-rhui-rpms 211 k
 apr-util-bdb       x86_64 1.6.1-20.el9_2.1   @rhel-9-appstream-rhui-rpms  15 k
 apr-util-openssl   x86_64 1.6.1-20.el9_2.1   @rhel-9-appstream-rhui-rpms  23 k
 httpd-core         x86_64 2.4.53-11.el9_2.5  @rhel-9-appstream-rhui-rpms 4.6 M
 httpd-filesystem   noarch 2.4.53-11.el9_2.5  @rhel-9-appstream-rhui-rpms 400  
 httpd-tools        x86_64 2.4.53-11.el9_2.5  @rhel-9-appstream-rhui-rpms 198 k
 mailcap            noarch 2.1.49-5.el9       @rhel-9-baseos-rhui-rpms     78 k
 mod_http2          x86_64 1.15.19-4.el9_2.4  @rhel-9-appstream-rhui-rpms 385 k
 mod_lua            x86_64 2.4.53-11.el9_2.5  @rhel-9-appstream-rhui-rpms 142 k
 redhat-logos-httpd noarch 90.4-1.el9         @rhel-9-appstream-rhui-rpms  12 k

Transaction Summary
================================================================================
Remove  12 Packages

Freed space: 6.0 M
Is this ok [y/N]: y
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                        1/1 
  Running scriptlet: httpd-2.4.53-11.el9_2.5.x86_64                        1/12 
  Erasing          : httpd-2.4.53-11.el9_2.5.x86_64                        1/12 
  Running scriptlet: httpd-2.4.53-11.el9_2.5.x86_64                        1/12 
  Erasing          : mod_lua-2.4.53-11.el9_2.5.x86_64                      2/12 
  Erasing          : mod_http2-1.15.19-4.el9_2.4.x86_64                    3/12 
  Erasing          : redhat-logos-httpd-90.4-1.el9.noarch                  4/12 
  Erasing          : httpd-core-2.4.53-11.el9_2.5.x86_64                   5/12 
  Erasing          : httpd-tools-2.4.53-11.el9_2.5.x86_64                  6/12 
  Erasing          : mailcap-2.1.49-5.el9.noarch                           7/12 
  Erasing          : httpd-filesystem-2.4.53-11.el9_2.5.noarch             8/12 
  Erasing          : apr-util-1.6.1-20.el9_2.1.x86_64                      9/12 
  Erasing          : apr-util-bdb-1.6.1-20.el9_2.1.x86_64                 10/12 
  Erasing          : apr-1.7.0-11.el9.x86_64                              11/12 
  Erasing          : apr-util-openssl-1.6.1-20.el9_2.1.x86_64             12/12 
  Running scriptlet: apr-util-openssl-1.6.1-20.el9_2.1.x86_64             12/12 
  Verifying        : apr-1.7.0-11.el9.x86_64                               1/12 
  Verifying        : apr-util-1.6.1-20.el9_2.1.x86_64                      2/12 
  Verifying        : apr-util-bdb-1.6.1-20.el9_2.1.x86_64                  3/12 
  Verifying        : apr-util-openssl-1.6.1-20.el9_2.1.x86_64              4/12 
  Verifying        : httpd-2.4.53-11.el9_2.5.x86_64                        5/12 
  Verifying        : httpd-core-2.4.53-11.el9_2.5.x86_64                   6/12 
  Verifying        : httpd-filesystem-2.4.53-11.el9_2.5.noarch             7/12 
  Verifying        : httpd-tools-2.4.53-11.el9_2.5.x86_64                  8/12 
  Verifying        : mailcap-2.1.49-5.el9.noarch                           9/12 
  Verifying        : mod_http2-1.15.19-4.el9_2.4.x86_64                   10/12 
  Verifying        : mod_lua-2.4.53-11.el9_2.5.x86_64                     11/12 
  Verifying        : redhat-logos-httpd-90.4-1.el9.noarch                 12/12 
Installed products updated.

Removed:
  apr-1.7.0-11.el9.x86_64                                                       
  apr-util-1.6.1-20.el9_2.1.x86_64                                              
  apr-util-bdb-1.6.1-20.el9_2.1.x86_64                                          
  apr-util-openssl-1.6.1-20.el9_2.1.x86_64                                      
  httpd-2.4.53-11.el9_2.5.x86_64                                                
  httpd-core-2.4.53-11.el9_2.5.x86_64                                           
  httpd-filesystem-2.4.53-11.el9_2.5.noarch                                     
  httpd-tools-2.4.53-11.el9_2.5.x86_64                                          
  mailcap-2.1.49-5.el9.noarch                                                   
  mod_http2-1.15.19-4.el9_2.4.x86_64                                            
  mod_lua-2.4.53-11.el9_2.5.x86_64                                              
  redhat-logos-httpd-90.4-1.el9.noarch                                          

Complete!
[student@ip-172-31-88-88 ~]$
```

## Lab
1. Using the `dnf` command, find out information about the *httpd* package
2. Install the *httpd* package
3. Remove the *httpd* package

## Conclusion
In this lab, we have seen how to add and remove packages on Linux systems.  High level tools like **dnf** and **apt-get** are preferred over low level tools such as **rpm** and **dpkg** due to the ability to resolve dependencies automatically.  

## Reference

* [Linux Fundamentals Textbook](https://linux-training.be/linuxfun.pdf)
  * Chapter 5.8 - Package Management
