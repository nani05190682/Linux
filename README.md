[root@localhost ~]#

[username@hostname (~)home_directory] Shell

Shell, acts as a interpreter between user and Kernel
#- Root User ( Administrator )
$- Normal User 
![image](https://user-images.githubusercontent.com/87597729/177003951-43faeae6-c91a-49f4-a6b7-a39adc1def23.png)

![image](https://user-images.githubusercontent.com/87597729/177003964-dfc0fdf2-9c1e-4fc6-afb9-bad8245b0253.png)

#Switching between Accounts

# Switching between Accounts

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

![image](https://user-images.githubusercontent.com/87597729/177003992-f5669099-a15e-45f1-be31-cc99e6129401.png)
