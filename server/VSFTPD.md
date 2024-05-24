# VSFTPD ##
 
Package : VSFTPD

Port: 

Ø 21 – FTP

Ø 20 – FTP Data

Configuration file : /etc/vsftpd/vsftpd.conf

Service : vsftpd


Downloading files from FTP


![image](https://github.com/nani05190682/Linux/assets/87597729/c177e848-e5c2-46f8-8dc9-7b2e76c66ae4)


Uploading files from FTP

![image](https://github.com/nani05190682/Linux/assets/87597729/f67b963e-f514-464f-b30d-6d5d0de7eb4a)



# Users that are not allowed to login via ftp


User add to vim /etc/vsftpd/ftpusers. (server)

![image](https://github.com/nani05190682/Linux/assets/87597729/4bcba0ac-8e44-4680-9653-b93795174fff)



Client :

![image](https://github.com/nani05190682/Linux/assets/87597729/5930845c-d0b5-4df2-a102-f5a30d5d7dbf)



Users allowed to login via ftp:

Users add to vim /etc/vsftpd/user_list (server)


# If userlist_deny=NO, only allow users in this file


![image](https://github.com/nani05190682/Linux/assets/87597729/9bdbb4f3-bbdb-4cc9-b512-fbedec8d416d)



Client :


![image](https://github.com/nani05190682/Linux/assets/87597729/a30307eb-239b-487d-95a6-e5ecbc77ec77)




Open vim /etc/vsftpd/vsftpd.conf  file chage to userlist_enables=YES ( server)

# If userlist_deny=YES (default), never allow users in this file, and do not even prompt for a password.


![image](https://github.com/nani05190682/Linux/assets/87597729/103833e0-2d0a-4e8a-8384-5b26da2a2806)



Client :

![image](https://github.com/nani05190682/Linux/assets/87597729/186c2b43-e234-42a8-89fd-d6826f31a2c3)





