# Secure Shell (SSH)

• Log into a remote system using ssh to run commands from a shell prompt. 

• Set up ssh to allow secure password-free logins by using a private authentication key file.

• Customize sshd configuration to restrict direct logins as root or to disable password-based authentication.



# What is the OpenSSH secure shell (SSH)?


• The term OpenSSH refers to the software implementation of the Secure Shell software used in the system.

• The OpenSSH Secure Shell, ssh, is used to securely run a shell on a remote system.

If you have a user account on a remote Linux system providing SSH services, ssh is the command normally used to remotely log into that system.



# Secure Shell examples 

Create a remote interactive shell as the current user, then return to your previous shell when done with the exit command.
![image](https://user-images.githubusercontent.com/87597729/182511619-f125f1d6-48b0-4768-b3e9-85b796215b1f.png)



Connect to a remote shell as a different user (remoteuser) on a selected host (remotehost):
![image](https://user-images.githubusercontent.com/87597729/182511627-b68d917d-73dd-4321-8fd5-0cce728100f3.png)




Execute a single command (hostname) on a remote host (remotehost) and as a remote user (remoteuser) in a way that returns the output to the local display: 
![image](https://user-images.githubusercontent.com/87597729/182511636-6c2678f7-4ded-4c2a-94f2-0fe99278d001.png)



The w command displays a list of users currently logged into the computer. This is especially useful to show which users are logged in using ssh from which remote locations, and what they are doing.
![image](https://user-images.githubusercontent.com/87597729/182511648-0be75c0b-9c54-44f4-9d3a-3d547c5beec8.png)








# SSH host keys

• SSH secures communication through public-key encryption.

• ssh client connects to an SSH server, before the client logs in, the server sends it a copy of its public key. 

• This is used to set up the secure encryption for the communication channel and to authenticate the server to the client. 


• The first time a user uses ssh to connect to a particular server, the ssh command stores the server's public key in the user's ~/.ssh/known_hosts file.

• Every time the user connects after that, the client makes sure it gets the same public key from the server by comparing the server's entry in the ~/.ssh/known_hosts file to the public key the server sent.

. If the keys do not match, the client assumes that the network traffic is being hijacked or that the server has been compromised, and breaks the connection

• Host IDs are stored in ~/.ssh/known_hosts on your local client system:

![image](https://user-images.githubusercontent.com/87597729/182511664-4e83e80a-3af3-44d1-ae30-e0ae98790516.png)



• Host keys are stored in /etc/ssh/ssh_host_key* on the SSH server.

![image](https://user-images.githubusercontent.com/87597729/182511683-997253ec-eb79-4c66-9712-40fcb794ebad.png)



## Configuring SSH Key-based Authentication 

# SSH key-based authentication


• Users can authenticate ssh logins without a password by using public key authentication.

• ssh allows users to authenticate using a private-public key scheme. 

• This means that two keys are generated, a private key and a public key. 

• The private key file is used as the authentication credential, and like a password, must be kept secret and secure.

The public key is copied to systems the user wants to log into, and is used to verify the private key. 

• The public key does not need to be secret. 

• An SSH server that has the public key can issue a challenge that can only be answered by a system holding your private key. . As a result, you can authenticate using the presence of your key. 

• Key generation is done using the ssh-keygen command. This generates the private key ~/.ssh/id_rsa and the public key ~/.ssh/id_rsa.pub. 


# LAB Exercise:

1. Login to your host and create a private and public key.
![image](https://user-images.githubusercontent.com/87597729/182511763-74c2ee2b-890f-4a6f-b5ae-faa7eda043e9.png)
	


Copy the public key to remote host.

![image](https://user-images.githubusercontent.com/87597729/182511775-7bc0dcd6-af6b-496f-bc64-b0f93f9005d2.png)




2. Disable ssh login for the root user and password-based SSH authentication on serverX.

![image](https://user-images.githubusercontent.com/87597729/182511800-431751b9-0a9c-45d0-90c4-20b4415bdc72.png)




Restart the SSHD service
![image](https://user-images.githubusercontent.com/87597729/182511815-9dd59d70-6986-4ef4-818e-f15df5790119.png)



Try login to the server and check if you are able to login.

# LAB:
# Change the default port 22 to port 10022
