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

To start the suspended process running in the background, use the **bg** command with the samejob ID.
![image](https://user-images.githubusercontent.com/87597729/182024815-92b394ee-4604-44fa-a36b-0e7fc73ba0cd.png)


# Practice: Background and Foreground Processes
# Lab
Log in as student to serverX. Begin in student's home directory.

1.  Open two terminal windows, side by side, to be referred to as left and right.
2.   In the left window, start a process that continuously appends the word "rock" and a space to the file ~/outfile at one-second intervals. The complete command set must be contained in parentheses for job control to interpret the set as a single job.
![image](https://user-images.githubusercontent.com/87597729/182024868-daa21934-186f-44b9-a754-a6a96267f6f7.png)
3.  In the right window, use tail to confirm that the new process is writing to the file.
![image](https://user-images.githubusercontent.com/87597729/182024979-1f5316c9-7ab8-4e8e-9d10-02da8cfd48e5.png)
4.   In the left window, suspend the running process. The shell returns the job ID in square brackets. In the right window, confirm that the process output has stopped.
![image](https://user-images.githubusercontent.com/87597729/182025000-db46d969-f9d8-4dfd-9f95-4d066f970c74.png)

5. In the left window, view the jobs list. The + denotes the current job. Restart the job in the background. In the right window, confirm that the process output is again active. 
 ![image](https://user-images.githubusercontent.com/87597729/182025028-419879f9-2eec-4e42-bf9e-986b6d6122d2.png)

6. In the left window, start two more processes to append to the same output file. Replace "rock" with "paper," and then with "scissors." To properly background the process, the complete command set must be contained in parentheses and ended with an ampersand.
![image](https://user-images.githubusercontent.com/87597729/182025055-19b52587-22dd-465c-9607-225939eaafd2.png)

7. In the left window, view jobs to see all three processes "Running". In the right window, confirm that all three processes are appending to the file.
![image](https://user-images.githubusercontent.com/87597729/182025068-5ec70edd-7951-453a-b15e-2ff4059e07a0.png)

8. Using only commands previously learned, suspend the "rock" process. In the left window, foreground the job, using the job ID determined from the jobs listing, then suspend it using Ctrl+z. Confirm that the "rock" process is "Stopped". In the right window, confirm that "rock" output is no longer active.
![image](https://user-images.githubusercontent.com/87597729/182025088-1e6e4305-c22a-4604-9170-60261fc20495.png)

9. End the "paper" process. In the left window, foreground the job, then terminate it using Ctrl+c. Confirm that the "paper" process has disappeared. In the right window, confirm that "paper" output is no longer active.

![image](https://user-images.githubusercontent.com/87597729/182025111-8ff23b56-b3a9-4f82-8bbd-819bc7941c05.png)

10.  In the left window, view the remaining jobs using ps. The suspended job has state T. Theother background job is sleeping (S), since ps is "on cpu" (R) while displaying.
![image](https://user-images.githubusercontent.com/87597729/182025124-d0ecec80-6751-479a-9670-9a17ff28578d.png)

11.   Stop the remaining two jobs. In the left window, foreground either job. Terminate it using Ctrl+c. Repeat with the remaining job. The "Stopped" job temporarily restarts when foregrounded. Confirm that no jobs remain and that output has stopped.
![image](https://user-images.githubusercontent.com/87597729/182025147-4eba7751-74a5-4cd1-87cd-7e7748487e98.png)

12.    In the right window, stop the tail command. Close extra terminal windows.
![image](https://user-images.githubusercontent.com/87597729/182025158-42fe7d18-f2c6-49ee-9251-120baa57e626.png)

# Killing Processes
# Process control using signals
![image](https://user-images.githubusercontent.com/87597729/182026417-d450d6ce-b134-4774-b3bd-e95ae33e6430.png)

The kill command sends a signal to a process by ID. Despite its name, the kill command can be used for sending any signal, not just those for terminating programs.
![image](https://user-images.githubusercontent.com/87597729/182026458-badb3317-2282-4646-9631-67ccf61d599e.png)

Use killall to send a signal to one or more processes matching selection criteria, such as a command name, processes owned by a specific user, or all system-wide processes.
![image](https://user-images.githubusercontent.com/87597729/182026503-27cb49e6-a711-4373-8f13-32b3f7ec98d3.png)

The pkill command, like killall, can signal multiple processes. pkill uses advanced selection criteria, which can include combinations of:
   Command — Processes with a pattern-matched command name.
   UID — Processes owned by a Linux user account, effective or real.
   GID — Processes owned by a Linux group account, effective or real.
   Parent — Child processes of a specific parent process.
   Terminal — Processes running on a specific controlling terminal.

![image](https://user-images.githubusercontent.com/87597729/182026520-75c85342-edd6-4ccb-b1cf-3f8aec07488b.png)
![image](https://user-images.githubusercontent.com/87597729/182026525-86b4549a-6249-4337-82e2-9ee8ff38828f.png)

# Logging users out administratively
1. The w command views users currently logged into the system and their cumulative activities.

2. Remote users display their connecting system name in the FROM column when using the -f option
![image](https://user-images.githubusercontent.com/87597729/182026603-74c1a498-aef1-4392-b725-7890ae12ebbc.png)

Processes and sessions can be individually or collectively signaled. To terminate all processes for one user, use the pkill command.
![image](https://user-images.githubusercontent.com/87597729/182026631-a559d32c-0216-424f-a82c-ef6cb8174607.png)
![image](https://user-images.githubusercontent.com/87597729/182026638-29c95eab-e6cd-4ac7-8df5-2cbeeb6dc32a.png)
![image](https://user-images.githubusercontent.com/87597729/182026654-92173e3f-e777-4b2b-a60c-2229580821c5.png)
![image](https://user-images.githubusercontent.com/87597729/182026658-4db01899-afd6-4646-a433-0d2f9c42d027.png)

# Monitoring Process Activity
# Load average
![image](https://user-images.githubusercontent.com/87597729/182026715-fbec706f-6cf5-4a2f-a0a5-e0d4ccf438b7.png)












































