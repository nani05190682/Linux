Server side:

1. Install vsftpd
# yum install vsftpd -y

# systemctl enable vsftpd
# systemctl start vsftpd



# vim /etc/vsftp/vsftp.conf
anonymous_enable=yes
=========================================================================



[root@server Packages]# rpm -ivh ftp-0.17-89.el9.x86_64.rpm
Verifying...                          ################################# [100%]
Preparing...                          ################################# [100%]
Updating / installing...
   1:ftp-0.17-89.el9                  ################################# [100%]


[root@server Packages]# ftp 192.168.224.128
Connected to 192.168.224.128 (192.168.224.128).
220 (vsFTPd 3.0.3)
Name (192.168.224.128:root): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
227 Entering Passive Mode (192,168,224,128,209,239).
150 Here comes the directory listing.
drwxrwxrwx    7 0        0            4096 Dec 19 04:32 pub
226 Directory send OK.
ftp>




# systemctl disable firewalld
# systemctl stop firewalld
# systemctl status firewalld


# vi /etc/sysconfig/selinux
SELINUX=disabled


cd  /etc/yum.repos.d

# vim client.repo

[root@server yum.repos.d]# cat client.repo
[baseos]
name=baseos
baseurl=ftp://192.168.224.128/pub/BaseOS/
enabled=1
gpgcheck=0


[Appstream]
name=Appstream
baseurl=ftp://192.168.224.128/pub/AppStream/
enabled=1
gpgcheck=0

[root@server yum.repos.d]#


