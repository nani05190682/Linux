# Linux

Linux Administrator Account / Normal user Account


Shell


[root@localhost ~]#

[username@hostname (~)home_directory] Shell

Shell, acts as a interpreter between user and Kernel
# - Root User ( Administrator )
$ - Normal User 
![image](https://user-images.githubusercontent.com/87597729/177003757-ce59585a-a191-489a-9226-b5fa77445c33.png)

![image](https://user-images.githubusercontent.com/87597729/177003776-32b71ad3-94da-46e2-9358-d8eb7449f2ca.png)

#Switching between Accounts


[root@localhost ~]# su - prashanth
[prashanth@vt ~]$ whoami
prashanth
[prashanth@vt ~]$ exit
logout
[root@localhost ~]#
[root@localhost ~]# su - jp
Last login: Fri Jul  1 23:49:18 PDT 2022 on pts/1
[jp@vt ~]$ whoami
jp
[jp@vt ~]$ su - punith
Password:
Last login: Fri Jul  1 23:48:55 PDT 2022 on pts/1
[punith@vt ~]$ whoami
punith
[punith@vt ~]$ su - jp
Password:
Last login: Fri Jul  1 23:50:01 PDT 2022 on pts/1
[jp@vt ~]$ whoami
jp
[jp@vt ~]$ su -
Password:
Last login: Fri Jul  1 22:34:21 PDT 2022 on pts/1
[root@vt ~]#![image](https://user-images.githubusercontent.com/87597729/177003815-dd93d9bc-5b58-4d77-875b-0d9d55e04389.png)

