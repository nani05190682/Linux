# VSFTPD ##
 
Package : VSFTPD
Port: 
Ø 21 – FTP
Ø 20 – FTP Data
Configuration file : /etc/vsftpd/vsftpd.conf
Service : vsftpd


Downloading files from FTP



Uploading files from FTP



# Users that are not allowed to login via ftp

User add to vim /etc/vsftpd/ftpusers. (server)



Client :



Users allowed to login via ftp:

Users add to vim /etc/vsftpd/user_list (server)

# If userlist_deny=NO, only allow users in this file



Client :





Open vim /etc/vsftpd/vsftpd.conf  file chage to userlist_enables=YES ( server)

# If userlist_deny=YES (default), never allow users in this file, and do not even prompt for a password.



Client :




