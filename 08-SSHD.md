#Secure Shell (SSH)

• Log into a remote system using ssh to run commands from a shell prompt. 

• Set up ssh to allow secure password-free logins by using a private authentication key file.

• Customize sshd configuration to restrict direct logins as root or to disable password-based authentication.



# What is the OpenSSH secure shell (SSH)?


The term OpenSSH refers to the software implementation of the Secure Shell software used in the system.

The OpenSSH Secure Shell, ssh, is used to securely run a shell on a remote system.

If you have a user account on a remote Linux system providing SSH services, ssh is the command normally used to remotely log into that system.



# Secure Shell examples 

Create a remote interactive shell as the current user, then return to your previous shell when done with the exit command.



Connect to a remote shell as a different user (remoteuser) on a selected host (remotehost):




Execute a single command (hostname) on a remote host (remotehost) and as a remote user (remoteuser) in a way that returns the output to the local display: 



The w command displays a list of users currently logged into the computer. This is especially useful to show which users are logged in using ssh from which remote locations, and what they are doing.








# SSH host keys

SSH secures communication through public-key encryption.

ssh client connects to an SSH server, before the client logs in, the server sends it a copy of its public key. 

This is used to set up the secure encryption for the communication channel and to authenticate the server to the client. 


The first time a user uses ssh to connect to a particular server, the ssh command stores the server's public key in the user's ~/.ssh/known_hosts file.

Every time the user connects after that, the client makes sure it gets the same public key from the server by comparing the server's entry in the ~/.ssh/known_hosts file to the public key the server sent.

. If the keys do not match, the client assumes that the network traffic is being hijacked or that the server has been compromised, and breaks the connection

Host IDs are stored in ~/.ssh/known_hosts on your local client system:




Host keys are stored in /etc/ssh/ssh_host_key* on the SSH server.




## Configuring SSH Key-based Authentication 

# SSH key-based authentication


Users can authenticate ssh logins without a password by using public key authentication.

ssh allows users to authenticate using a private-public key scheme. 

This means that two keys are generated, a private key and a public key. 

The private key file is used as the authentication credential, and like a password, must be kept secret and secure.

The public key is copied to systems the user wants to log into, and is used to verify the private key. 

The public key does not need to be secret. 

An SSH server that has the public key can issue a challenge that can only be answered by a system holding your private key. . As a result, you can authenticate using the presence of your key. 

Key generation is done using the ssh-keygen command. This generates the private key ~/.ssh/id_rsa and the public key ~/.ssh/id_rsa.pub. 


LAB Exercise:

	1. Login to your host and create a private and public key.
	


Copy the public key to remote host.





2. Disable ssh login for the root user and password-based SSH authentication on serverX.





Restart the SSHD service



Try login to the server and check if you are able to login.

# LAB:
# Change the default port 22 to port 10022
