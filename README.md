[root@localhost ~]#

[username@hostname (~)home_directory] Shell

Shell, acts as a interpreter between user and Kernel
#- Root User ( Administrator )
$- Normal User 
![image](https://user-images.githubusercontent.com/87597729/177003951-43faeae6-c91a-49f4-a6b7-a39adc1def23.png)

![image](https://user-images.githubusercontent.com/87597729/177003964-dfc0fdf2-9c1e-4fc6-afb9-bad8245b0253.png)

#Switching between Accounts

# Switching between Accounts

![image](https://user-images.githubusercontent.com/87597729/177003992-f5669099-a15e-45f1-be31-cc99e6129401.png)


# Lab Exercise
1. Create the following user accounts

       normaluser1
      
       normaluser2
2. Set the password for the accounts

      normaluser1 -> password1 
      
      normaluser2 -> password2 
3. Check which user you are currently logged in by using "**whoami**" command
4. From root account switch to normaluser1
    
    Note: It will not prompt for the password as you are an administrator
    
5. From normaluser1 switch to normaluser2 account
6. Form normaluser2 switch to root

# Moniroting and Managing Linux Process

# Objectives
1. List and interpret basic information about processes running on the system.
2. Control processes in the shell's session using bash job control.
3. Terminate and control processes using signals.
4. Monitor resource usage and system load due to process activity.


# What is Process?

A process is a running instance of a launched, executable program. A process consists of:

• an address space of allocated memory,

• security properties including ownership credentials and privileges,

• one or more execution threads of program code, and

• the process state.


# How Process Works?

* An existing (parent) process duplicates its own address space (fork) to create a new (child)
process structure. 

* Every new process is assigned a unique process ID (PID) for tracking and security.

* The PID and the parent's process ID (PPID) are elements of the new process environment. 

* Any process may create a child process. All processes are descendants of the first system process, which is systemd(1) on a Red Hat Enterprise Linux 7 system.

# Process Life Cycle
![image](https://user-images.githubusercontent.com/87597729/182024374-8d55ea93-4fe0-484a-ad72-eb0443862735.png)


* Through the fork routine, a child process inherits security identities, previous and current file descriptors, port and resource privileges, environment variables, and program code.
* A child process may then exec its own program code. 
* Normally, a parent process sleeps while the child process runs, setting a request (wait) to be signaled when the child completes.
* Upon exit, the child process has already closed or discarded its resources and environment; the remainder is referred to as a zombie.\
* The parent, signaled awake when the child exited, cleans the remaining structure, then continues with its own program code execution.


# Process states

![image](https://user-images.githubusercontent.com/87597729/182024549-dd3745bc-3699-44ed-a94d-45aecb391b2d.png)

![image](https://user-images.githubusercontent.com/87597729/182024560-4a70217f-32dd-484c-b30c-3143280b66bd.png)

![image](https://user-images.githubusercontent.com/87597729/182024571-860f6f89-5713-470c-baef-247e19cc28cd.png)


# Listing processes
![image](https://user-images.githubusercontent.com/87597729/182024599-8143bc63-f7a4-419a-bc47-25a4aaa80e4b.png)
![image](https://user-images.githubusercontent.com/87597729/182024611-b6c95c09-2171-469b-b9c3-360761c2ff17.png)


# Controlling Jobs
# Running jobs in the background
![image](https://user-images.githubusercontent.com/87597729/182024642-1b928dc8-fb00-4df6-97f6-691afbdd3879.png)
# Viewing background Jobs
![image](https://user-images.githubusercontent.com/87597729/182024666-4fc680f8-cae7-462f-95e6-9c5699673eaf.png)

A background job can be brought to the foreground by using the fg command with its job ID
![image](https://user-images.githubusercontent.com/87597729/182024690-aeef180a-9f64-413d-abc7-50eeb1833dfd.png)

To send a foreground process to the background, first press the keyboard-generated suspend request **(Ctrl+z)** on the terminal.

![image](https://user-images.githubusercontent.com/87597729/182024730-4bc3e5d8-9f1a-4d97-87c3-407e5874e933.png)


















