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

An existing (parent) process duplicates its own address space (fork) to create a new (child)
process structure. 

Every new process is assigned a unique process ID (PID) for tracking and security.

The PID and the parent's process ID (PPID) are elements of the new process environment. 

Any process may create a child process. All processes are descendants of the first system process, which is systemd(1) on a Red Hat Enterprise Linux 7 system.

# Process Life Cycle
![image](https://user-images.githubusercontent.com/87597729/182024374-8d55ea93-4fe0-484a-ad72-eb0443862735.png)
















