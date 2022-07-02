

[root@vaultserver ~]# useradd class3
[root@vaultserver ~]# 
[root@vaultserver ~]# su - class3
[class3@vaultserver ~]$ 


# touch file_name - Creates empty file
example:
$ touch myfile
[class3@vaultserver ~]$ ls
myfile
[class3@vaultserver ~]$ 




# Create a hidden file.


[class3@vaultserver ~]$ touch .myfile2
[class3@vaultserver ~]$ ls
myfile
[class3@vaultserver ~]$ ls -a
.   .bash_logout   .bashrc  .config   myfile
..  .bash_profile  .cache   .mozilla  .myfile2
[class3@vaultserver ~]$ 


# Create multiple files


[class3@vaultserver ~]$ touch myfile{2..5}
[class3@vaultserver ~]$ ls
myfile  myfile2  myfile3  myfile4  myfile5
[class3@vaultserver ~]$ 




Check file type:


[class3@vaultserver ~]$ ls -l
total 0
drwxrwxr-x 2 class3 class3 6 Jun  5 07:49 mydir
-rw-rw-r-- 1 class3 class3 0 Jun  5 07:42 myfile
-rw-rw-r-- 1 class3 class3 0 Jun  5 07:45 myfile2
-rw-rw-r-- 1 class3 class3 0 Jun  5 07:45 myfile3
-rw-rw-r-- 1 class3 class3 0 Jun  5 07:45 myfile4
-rw-rw-r-- 1 class3 class3 0 Jun  5 07:45 myfile5


[class3@vaultserver ~]$ file mydir
mydir: directory
[class3@vaultserver ~]$ file myfile
myfile: empty
[class3@vaultserver ~]$ 




# Create content file on file


[class3@vaultserver ~]$ cat > textfile
This is my file


CTRL+D => Save


[class3@vaultserver ~]$ 




[class3@vaultserver ~]$ file textfile 
textfile: ASCII text
[class3@vaultserver ~]$ 




To view the file
[class3@vaultserver ~]$ cat textfile 
This is my file
[class3@vaultserver ~]$ 


Rename a file
# mv original_file new_file
# mv myfile mytextfile


Example2:


[class3@vaultserver ~]$ mv mytextfile /var/tmp/
[class3@vaultserver ~]$ ls
mydir  myfile2  myfile3  myfile4  myfile5  textfile
[class3@vaultserver ~]$ ls -l /var/tmp/mytextfile 
-rw-rw-r-- 1 class3 class3 0 Jun  5 07:42 /var/tmp/mytextfile
[class3@vaultserver ~]$ 


# Copy file


[class3@vaultserver ~]$ cp textfile textfile2
[class3@vaultserver ~]$ ls -l
total 8
drwxrwxr-x 2 class3 class3  6 Jun  5 07:49 mydir
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile2
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile3
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile4
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile5
-rw-rw-r-- 1 class3 class3 16 Jun  5 07:50 textfile
-rw-rw-r-- 1 class3 class3 16 Jun  5 08:02 textfile2
[class3@vaultserver ~]$ cat textfile
This is my file
[class3@vaultserver ~]$ cat textfile2
This is my file
[class3@vaultserver ~]$ 




# Copy directory


[class3@vaultserver ~]$ cp -r mydir mybackupdir
[class3@vaultserver ~]$ ls 
mybackupdir  mydir  myfile2  myfile3  myfile4  myfile5  textfile  textfile2
[class3@vaultserver ~]$ ls mybackupdir/
file1  file2  test1  test2
[class3@vaultserver ~]$ 




# Removing file


[class3@vaultserver ~]$ ls -l
total 8
drwxrwxr-x 4 class3 class3 58 Jun  5 08:05 mybackupdir
drwxrwxr-x 4 class3 class3 58 Jun  5 08:04 mydir
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile2
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile3
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile4
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile5
-rw-rw-r-- 1 class3 class3 16 Jun  5 07:50 textfile
-rw-rw-r-- 1 class3 class3 16 Jun  5 08:02 textfile2
[class3@vaultserver ~]$ rm textfile2 
[class3@vaultserver ~]$ ls -l
total 4
drwxrwxr-x 4 class3 class3 58 Jun  5 08:05 mybackupdir
drwxrwxr-x 4 class3 class3 58 Jun  5 08:04 mydir
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile2
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile3
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile4
-rw-rw-r-- 1 class3 class3  0 Jun  5 07:45 myfile5
-rw-rw-r-- 1 class3 class3 16 Jun  5 07:50 textfile




Removing the directory


[class3@vaultserver ~]$ rm -r mydir
[class3@vaultserver ~]$ ls
mybackupdir  myfile2  myfile3  myfile4  myfile5  textfile
[class3@vaultserver ~]$ 




Lab Exercise:

1. Create a new user "linadmin"
	1. Switch to linadmin
	2. Create a directory "mytest"
	3. Get inside the directory "mytest"
	4. Create mytextfile1 to mytextfile10
	5. Create a directory "backup" in the same path (/home/linadmin/mytest)
	6. Copy all mytextfile* files to "backup" directory
	7. Copy "backup" directory to "backup2"
	8. Move "backup2" to "new_backup"
	9. Remove the "backup" directory
	10. Create a file with content "Hello World" and name it as new_file.txt
	11. Check what type of file (new_file.txt)
	12. Create a hidden file with name hide.





File Permissions:

#File Permissions:
===============


# ls -l => long list


d | rwx | r-x | r-x. 2 root root 6 Dec 24 12:52 test-dir




D - directory [file or directory]
rwx - User Permission
r-x - Group Permission
r-x - others Permission
2 -  Hard Link
root - user
root - group
6 - size
Dec 24 12:52 - time stamp
test-dir - directory name


( r = read (4))
( w = write (2))
( x = execute (1))




-rw-r--r--. 1 root root 0 Dec 24 12:53 test-file


Umask:


[root@instance-1 file-perm]# umask
0022


File Permissions:


[root@instance-1 file-perm]# ls -l
total 0
drwxr-xr-x. 2 root root 6 Dec 24 12:52 test-dir
-rw-r--r--. 1 root root 0 Dec 24 12:53 test-file
[root@instance-1 file-perm]# 


Umask = 0022
Directory : 777
File: 666


Directory Permission = Default dir permission - umask value


777
 22
====
7|5|5
====


666
 22
===
644
===




Example:






Changing file permissions:


1. rwxrwxr— => 774
2. r-- |r—| -wx   => 443
3. rw-r—r-x   =>  645
4 rw- rwx — => 670


# chmod 774 file/dir_name
# chmod 443 file2
# chmod 645 file3




[root@rhel7 test]# chmod 640 file4 
[root@rhel7 test]# ls -l
total 0
-rwxrwxr--. 1 root root 0 Dec 28 12:39 file1
-r--r---wx. 1 root root 0 Dec 28 12:39 file2
-rw-r--r-x. 1 root root 0 Dec 28 12:39 file3
-rw-r-----. 1 root root 0 Dec 28 12:39 file4




Set read-only files for all the files on my current path.


[satya@rhel7 ~]$ chmod 400 *
[satya@rhel7 ~]$ ls -l
[satya@rhel7 ~]$ ls -l
total 0
-r--------. 1 satya satya 0 Dec 28 12:52 dfile1
-r--------. 1 satya satya 0 Dec 28 12:52 dfile10
-r--------. 1 satya satya 0 Dec 28 12:52 dfile2
-r--------. 1 satya satya 0 Dec 28 12:52 dfile3
-r--------. 1 satya satya 0 Dec 28 12:52 dfile4
-r--------. 1 satya satya 0 Dec 28 12:52 dfile5
-r--------. 1 satya satya 0 Dec 28 12:52 dfile6




Setting permissions along with sub-directories.
==============================================


[satya@rhel7 ~]$ chmod -R 700 test/
[satya@rhel7 ~]$ ls -l
total 0
drwx------. 7 satya satya 131 Dec 28 12:59 test
[satya@rhel7 ~]$ ls -l test/
total 0
drwx------. 2 satya satya 6 Dec 28 12:59 dir1
drwx------. 2 satya satya 6 Dec 28 12:59 dir2
drwx------. 2 satya satya 6 Dec 28 12:59 dir3
drwx------. 2 satya satya 6 Dec 28 12:59 dir4
drwx------. 2 satya satya 6 Dec 28 12:59 dir5
-rwx------. 1 satya satya 0 Dec 28 12:59 file1
-rwx------. 1 satya satya 0 Dec 28 12:59 file2
-rwx------. 1 satya satya 0 Dec 28 12:59 file3
-rwx------. 1 satya satya 0 Dec 28 12:59 file4
-rwx------. 1 satya satya 0 Dec 28 12:59 file5
[satya@rhel7 ~]$ 

Lab Exercise:


1. create a user ‘redhat’ and switch to the account.
2. Create a directory called “mydata”
3. Goto “mydata” and create 5 files start with “myfile”
4. Create 5 directories on the same path (/home/redhat/mydata) with the name mydir[1..5]
5. Create 5 files again with the name starts with “gnome” and extension with .pdf
6. Copy all the pdf files to “mydir2”
7. Copy all the myfile[1-5] to mydir1
8. Change the director permission as follows
 8.1) mydir1: rwx | r-x |r— ( along with files inside this directory))
 8.2) mydir2 : rwx|r—|r— ( along with files inside this directory))
 8.3) myfile1 : rwx|rwx|—
  8.4)myfile2 : r—|r— |—



[root@localhost owner]# chgrp devops file1
[root@localhost owner]# ls -l
total 0
-rw-r--r--. 1 root devops 0 May 25 05:38 file1
[root@localhost owner]#

[root@localhost owner]# chown dinesh file1
[root@localhost owner]# ls -l
total 0
-rw-r--r--. 1 dinesh devops 0 May 25 05:38 file1
[root@localhost owner]#

[root@localhost owner]# chown karthik:murugan file1
[root@localhost owner]# ls -l
total 0
-rw-r--r--. 1 karthik murugan 0 May 25 05:38 file1
[root@localhost owner]#

[root@localhost owner]# chown karthik:murugan file1
[root@localhost owner]# ls -l
total 0
-rw-r--r--. 1 karthik murugan 0 May 25 05:38 file1
[root@localhost owner]# 


Changing Ownership for directory:



[root@localhost owner]# chown -R dinesh:devops test/
[root@localhost owner]# ls -l
total 44
-rw-r--r--. 1 dinesh root       0 May 25 05:38 file1
drwxr-xr-x. 2 dinesh devops 24576 May 25 05:46 test
[root@localhost owner]# ls -l |head
total 44
-rw-r--r--. 1 dinesh root       0 May 25 05:38 file1
drwxr-xr-x. 2 dinesh devops 24576 May 25 05:46 test
[root@localhost owner]# ls -l test/|head
total 0
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file1
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file10
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file100
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file1000
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file101
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file102
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file103
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file104
-rw-r--r--. 1 dinesh devops 0 May 25 05:46 file105
[root@localhost owner]#


## VI Editor


Command: (ESC) 
1. Copy (esc + yy) (esc +100yy) 
      2. Paste (esc + p)  
      3. Delete (esc +dd ) 
      4. Undo (esc + u) 
      5. Redo (ctrl +r ) 
      6. Search (/search_string): %s/earch_string/replace_string/i 
          %s/testing/replacing/gi 
 
 
Insert Mode: (i) 
 


 
Execute Mode: ( esc+  shift + : ) 
1. Save (:w!) 
2. Quit (:q!) 
3. Save and Quit (:wq!) 
4. Search and Replace  
:%s/Message2/Linux
:%s/Message2/Linux/g
:%s/Message2/linux/gi

5. Line numbers => (: set nu) 
6: Goto line => esc + : 15 


Command Mode: (ESC)


1. Copy : Esc + yy to copy a line from cursor point
# esc +nyy copies n number of lines  


2. Paste
esc+p => paste the copied lines


3. Delete => esc + dd  deletes a line from cursor point
Esc + 2dd, deletes 2 lines from cursor point


4. Undo : Esc +u 


5.Redo : CRTL + r 


6. Search : forward slash with search string.


/line




Insert Mode: (I)




Execute Mode (esc + shiit +:)


Save : w
quit! : q
Save and quit : wq
Search and replace : %s/search_string/replace_string

:%s/Message2/Linux
:%s/Message2/Linux/g
:%s/Message2/linux/gi


Line numbers : set nu
Goto specific line : :line_number






Command: (ESC) 
1. Copy (esc + yy) (esc +100yy) 
      2. Paste (esc + p)  
      3. Delete (esc +dd ) 
      4. Undo (esc + u) 
      5. Redo (ctrl +r ) 
      6. Search (/search_string): %s/earch_string/replace_string/i 
          %s/testing/replacing/gi 
 
 
Insert Mode: (i) 
 
 
Execute Mode: ( esc+  shift + : ) 
1. Save (:w!) 
2. Quit (:q!) 
3. Save and Quit (:wq!) 
4. Search and Replace  
5. Line numbers => (: set nu) 
6: Goto line => esc + : 15 


## Compression Utilities


1. gzip => File compression
 
[testuser@vaultserver ~]$ seq 100000000 > myfile
[testuser@vaultserver ~]$ ls -lh
total 1.0G
-rw-rw-r-- 1 testuser testuser 848M Jun 10 07:43 myfile
[testuser@vaultserver ~]$


[testuser@vaultserver ~]$ gzip myfile 
[testuser@vaultserver ~]$ ls -lh
total 212M
-rw-rw-r-- 1 testuser testuser 212M Jun 10 07:43 myfile.gz
[testuser@vaultserver ~]$ 




Example2:


[testuser@vaultserver ~]$ fallocate -l 1g vaithee.img
[testuser@vaultserver ~]$ ls -lh vaithee.img 
-rw-rw-r-- 1 testuser testuser 1.0G Jun 10 08:04 vaithee.img
[testuser@vaultserver ~]$ gzip vaithee.img 
[testuser@vaultserver ~]$ ls -lh vaithee.img.gz 
-rw-rw-r-- 1 testuser testuser 1018K Jun 10 08:04 vaithee.img.gz
[testuser@vaultserver ~]$ ls -l
total 434612
-rw-rw-r-- 1 testuser testuser 443995726 J	un 10 07:59 backup.tar
-rw-rw-r-- 1 testuser testuser   1042081 Jun 10 08:04 vaithee.img.gz
[testuser@vaultserver ~]$ ls -lh vaithee.img.gz 
-rw-rw-r-- 1 testuser testuser 1018K Jun 10 08:04 vaithee.img.gz
[testuser@vaultserver ~]$ gunzip vaithee.img.gz 
[testuser@vaultserver ~]$ ls -lh vaithee.img
-rw-rw-r-- 1 testuser testuser 1.0G Jun 10 08:04 vaithee.img
[testuser@vaultserver ~]$ 




# View the compressed file.


[testuser@vaultserver ~]$ zcat myfile.gz |head
1
2
3
4
5
6
7
8
9
10
[testuser@vaultserver ~]$ 




Unzip:


[testuser@vaultserver ~]$ gunzip myfile.gz 
[testuser@vaultserver ~]$ ls -lh
total 848M
-rw-rw-r-- 1 testuser testuser 848M Jun 10 07:43 myfile
[testuser@vaultserver ~]$ 




[testuser@vaultserver ~]$ gzip -c myfile > /tmp/myfile.gz
[testuser@vaultserver ~]$ ls -lh /tmp/myfile.gz 
-rw-rw-r-- 1 testuser testuser 212M Jun 10 07:51 /tmp/myfile.gz
[testuser@vaultserver ~]$ ls -lh myfile 
-rw-rw-r-- 1 testuser testuser 848M Jun 10 07:43 myfile
[testuser@vaultserver ~]$ > myfile 
[testuser@vaultserver ~]$ ls -lh myfile 
-rw-rw-r-- 1 testuser testuser 0 Jun 10 07:52 myfile
[testuser@vaultserver ~]$ 


2. tar => Directory Compression tool


[testuser@vaultserver ~]$ tar -czvf backup.tar backup
backup/
backup/myfile
backup/myfile2
[testuser@vaultserver ~]$ ls -lh
total 424M
drwxrwxr-x 2 testuser testuser   35 Jun 10 07:57 backup
-rw-rw-r-- 1 testuser testuser 424M Jun 10 07:59 backup.tar
[testuser@vaultserver ~]$ 




View the tar file:


Create Tar file:
==============


[testuser@vaultserver ~]$ tar -tvf backup.tar 
drwxrwxr-x testuser/testuser 0 2021-06-10 07:57 backup/
-rw-rw-r-- testuser/testuser 888888898 2021-06-10 07:56 backup/myfile
-rw-rw-r-- testuser/testuser 888888898 2021-06-10 07:57 backup/myfile2
[testuser@vaultserver ~]$ 




Extract file:
=============


[testuser@vaultserver ~]$ tar -xzvf backup.tar 
backup/
backup/myfile
backup/myfile2
[testuser@vaultserver ~]$ ls
backup  backup.tar
[testuser@vaultserver ~]$ ls -ltr
total 433592
drwxrwxr-x 2 testuser testuser        35 Jun 10 07:57 backup
-rw-rw-r-- 1 testuser testuser 443995726 Jun 10 07:59 backup.tar
[testuser@vaultserver ~]$ du -sh backup
1.7G backup
[testuser@vaultserver ~]$ 




C-  create
Z - compress file in zip format
v - verbose
f - file
x - extract


User Adminstration:

1. /etc/passwd - user information
2. /etc/shadow - user password information
3. /etc/group - group information
4. /etc/gshadow - group password information

testuser2:x:2019:2023::/home/testuser2:/bin/bash

username
password reference to shadow file
uid (u)
gid (g)
user comments (c)
user's home directory (d)
user's login shell (s)

Note: Whenever you create a user account by default with the same the group
will be created, that's basically a user's private group/ primary group.


testuser2:x:2019:2023::/home/testuser2:/bin/bash

Modification:
# usermod

Changing uid:
# usermod -u 2025 testuser2

[root@vaultserver ~]# usermod -u 2025 testuser2
[root@vaultserver ~]# tail -1 /etc/passwd
testuser2:x:2025:2023::/home/testuser2:/bin/bash
[root@vaultserver ~]#

Change GID
# groupmod -g 2025 testuser2
[root@vaultserver ~]# tail -1 /etc/passwd
testuser2:x:2025:2025::/home/testuser2:/bin/bash
[root@vaultserver ~]#

Add Comments:
# usermod -c "This is created for useradministration" testuser2
[root@vaultserver ~]# usermod -c "This is created for useradministration" testuser2
[root@vaultserver ~]# tail -1 /etc/passwd
testuser2:x:2025:2025:This is created for useradministration:/home/testuser2:/bin/bash
[root@vaultserver ~]#

Directory:
[root@vaultserver ~]# usermod -d /var/tmp/testuser2 testuser2
[root@vaultserver ~]# tail -3 /etc/passwd
testuser2:x:2025:2025:This is created for useradministration:/var/tmp/testuser2:/bin/bash

How to check availble shells on my host
# cat /etc/shells


Change Shell
[root@vaultserver ~]# usermod -s /bin/csh testuser2
[root@vaultserver ~]# cat /etc/passwd |grep testuser2
testuser2:x:2025:2025:This is created for useradministration:/var/tmp/testuser2:/bin/csh
[root@vaultserver ~]#



Changing home directory for the user and copying .bashrc/.basc_logout and .bash_profile files from /etc/skell

# /etc/skell
[root@vaultserver ~]# usermod -d /var/test3 test3
[root@vaultserver ~]# tail -1 /etc/passwd
test3:x:2029:2029::/var/test3:/bin/bash
[root@vaultserver ~]# su - test3
Last login: Wed Jun 16 18:42:51 IST 2021 on pts/0
su: warning: cannot change directory to /var/test3: No such file or directory
-bash-4.2$

Step1: Check if the home directory exists

[root@vaultserver ~]# mkdir /var/test3
[root@vaultserver ~]# su - test3
Last login: Wed Jun 16 18:43:54 IST 2021 on pts/0
-bash-4.2$ touch file1
touch: cannot touch ‘file1’: Permission denied
-bash-4.2$

Step2: Check if the user is able to create files on his home directory


[root@vaultserver ~]# ls -ld /var/test3/
drwxr-xr-x 2 root root 6 Jun 16 18:45 /var/test3/

Change the ownership:

[root@vaultserver ~]# chown test3:test3 /var/test3/
[root@vaultserver ~]# ls -ld /var/test3/
drwxr-xr-x 2 test3 test3 6 Jun 16 18:45 /var/test3/
[root@vaultserver ~]#

[root@vaultserver ~]# su - test3
Last login: Wed Jun 16 18:45:14 IST 2021 on pts/0
-bash-4.2$ touch file1
-bash-4.2$ ls -l
total 0
-rw-rw-r-- 1 test3 test3 0 Jun 16 18:48 file1
-bash-4.2$

### Check the useraccount comes with bash

[root@vaultserver etc]# cd /etc/skel/
[root@vaultserver skel]# ls -a
.  ..  .bash_logout  .bash_profile  .bashrc  .mozilla
[root@vaultserver skel]# cp .bash* /var/test3/
[root@vaultserver skel]# cd /var/test3/
[root@vaultserver test3]# ls -a
.  ..  .bash_history  .bash_logout  .bash_profile  .bashrc  .cache  .config  file1
[root@vaultserver test3]# ls -al
total 20
drwxr-xr-x   4 test3 test3  125 Jun 16 18:49 .
drwxr-xr-x. 23 root  root  4096 Jun 16 18:45 ..
-rw-------   1 test3 test3   18 Jun 16 18:48 .bash_history
-rw-r--r--   1 root  root    18 Jun 16 18:49 .bash_logout
-rw-r--r--   1 root  root   193 Jun 16 18:49 .bash_profile
-rw-r--r--   1 root  root   231 Jun 16 18:49 .bashrc
drwxrwxr-x   3 test3 test3   18 Jun 16 18:48 .cache
drwxrwxr-x   3 test3 test3   18 Jun 16 18:48 .config
-rw-rw-r--   1 test3 test3    0 Jun 16 18:48 file1
[root@vaultserver test3]# chown test3:test3 .bash*
[root@vaultserver test3]# ls -l
total 0
-rw-rw-r-- 1 test3 test3 0 Jun 16 18:48 file1
[root@vaultserver test3]# ls -al
total 20
drwxr-xr-x   4 test3 test3  125 Jun 16 18:49 .
drwxr-xr-x. 23 root  root  4096 Jun 16 18:45 ..
-rw-------   1 test3 test3   18 Jun 16 18:48 .bash_history
-rw-r--r--   1 test3 test3   18 Jun 16 18:49 .bash_logout
-rw-r--r--   1 test3 test3  193 Jun 16 18:49 .bash_profile
-rw-r--r--   1 test3 test3  231 Jun 16 18:49 .bashrc
drwxrwxr-x   3 test3 test3   18 Jun 16 18:48 .cache
drwxrwxr-x   3 test3 test3   18 Jun 16 18:48 .config
-rw-rw-r--   1 test3 test3    0 Jun 16 18:48 file1
[root@vaultserver test3]# su - test3
Last login: Wed Jun 16 18:48:29 IST 2021 on pts/0
[test3@vaultserver ~]$

Groups:
1. Primary Group :
User will have only one primary group.
Note : whenever user creates a file/directory, the group ownership will be his
primary group.

Change the primary group of the user:
=====================================
[root@vaultserver ~]# id william
uid=1002(william) gid=1002(william) groups=1002(william)
[root@vaultserver ~]# groupadd it
[root@vaultserver ~]# usermod -g it william
[root@vaultserver ~]# id william
uid=1002(william) gid=2031(it) groups=2031(it)
[root@vaultserver ~]#


2. Supplementary Group

User can be part of one or more supplementary group.
If user wants to access files/directories belongs to other groups, then he must have to
part of that group inorder to access file/directory

Adding users to supplementary group:
====================================
[root@vaultserver ~]# id william
uid=1002(william) gid=1002(william) groups=1002(william)
[root@vaultserver ~]# usermod -G it william 
[root@vaultserver ~]# id william
uid=1002(william) gid=1002(william) groups=1002(william),2031(it)
[root@vaultserver ~]# 



Process :

# ps -aef  => Lists all running process on the host

# ps -aef |grep sleep => it shows the process running with "sleep" string

Customizing ps outout


# kill  <pid> => Kill the process 
# kill -<signal> <pid>



# Kill signals 
	KILL 1
	KILL 15
	KILL 9

Kill the process with signals


	
# Run a process in background

# sleep 700 &
# sleep 900&
# sleep 1000&



# Running the process from background to foreground



$ top




$ top -p pid1,pid2,pid3



# nice and renice


IP Addressing:







Compression Utilities:



Compressing file to different path



Nullifying the file





Compressing Directory:

# tar -czvf backup.tar data ( c=create, v=verbose, f=file, z=zip)




List Compressed file




# tar xvf backup.tar ( x=xtract)




User Administration:









[root@localhost ~]# tail -1 /etc/passwd
demouser:x:3002:3002::/home/demouser:/bin/bash
[root@localhost ~]#


Issue1 : Check the home directory is created 

# mkdir /demouser


Issue2 : Check permission for the home directory
[root@localhost ~]# ls -ld /demouser/
drwxr-xr-x. 2 root root 6 Jun  3 05:10 /demouser/
[root@localhost ~]# chown demouser:demouser /demouser/
[root@localhost ~]#


Issue3 : Profile needs to be created

[root@localhost ~]# cd /etc/skel/
[root@localhost skel]# ls
[root@localhost skel]# ls -al
total 28
drwxr-xr-x.   3 root root   92 Apr 19 20:45 .
drwxr-xr-x. 145 root root 8192 Jun  3 05:09 ..
-rw-r--r--.   1 root root   18 Mar 31  2020 .bash_logout
-rw-r--r--.   1 root root  193 Mar 31  2020 .bash_profile
-rw-r--r--.   1 root root  231 Mar 31  2020 .bashrc
drwxr-xr-x.   4 root root   39 Apr 19 19:54 .mozilla
-rw-r--r--.   1 root root  658 Apr  7  2020 .zshrc
[root@localhost skel]# cp .bash* /demouser/
[root@localhost skel]# su - demouser
Last login: Fri Jun  3 05:12:02 PDT 2022 on pts/1
[demouser@localhost ~]$


User related configurations are available in "/etc/login.defs"


Change Supplementary

 group:
=========================
[root@localhost ~]# usermod -aG demousers demouser
[root@localhost ~]# id demouser
uid=3002(demouser) gid=3002(demouser) groups=3002(demouser),3004(demousers)
[root@localhost ~]# usermod -aG demousers demouser2
[root@localhost ~]# id demouser2
uid=3003(demouser2) gid=3003(demouser2) groups=3003(demouser2),3004(demousers)
[root@localhost ~]# ls -ld /de
demo-directory/ demouser/       demouser2/      dev/
[root@localhost ~]# ls -ld /demo-directory/
drwxr-xr-x. 2 root root 6 Jun  3 05:30 /demo-directory/
[root@localhost ~]# chgrp demousers /demo-directory/
[root@localhost ~]# ls -ld /demo-directory/
drwxr-xr-x. 2 root demousers 6 Jun  3 05:30 /demo-directory/
[root@localhost ~]# chmod 770 /demo-directory/
[root@localhost ~]# ls -ld /demo-directory/
drwxrwx---. 2 root demousers 6 Jun  3 05:30 /demo-directory/
[root@localhost ~]#

Change Primary Group:
====================
[root@localhost ~]# usermod -g org demouser
[root@localhost ~]# id demouser
uid=3002(demouser) gid=3005(org) groups=3005(org),3004(demousers)
[root@localhost ~]#







Adding Users to supplementry group:








Special Permissions:








'












RPM - Redhat Package Manager
zsh-5.0.2-34.el7_8.2.x86_64.rpm

zsh- Package Name
5.0.2- Major Version
34 - Minor Version
el7_8.2 - Enterprise Linux Version 7
x86_64 - > 64 bit










 


 
Installed Package:
 
# rpm -qa |grep gzip
gzip-1.5-10.el7.x86_64
 


 
# rpm -ql nfs-utils => Display all the files related to nfs-utils package
 


 
# rpm -Uvh <Package_name>




## Query file to get the package name




# Query Configuration file





# Query Documentation:





# Query dependency Package









Disk Administration


1, Attach a DISK 

2. Scan the disk and check the new disk is visible

3.  Create a Partition using fdisk command

# fdisk /dev/sdc

# n -> enter -> enter -> 1G -> w



4. Format the Disk with xfs filesystem




	6. Create a directory and mount the Filesystem
	#  mkdir /var/ftp/pub
	# mount /dev/sdc1 /var/ftp/pub
	
	7. Mount permanently in /etc/fstab file
	
	
	
	
	Links:
	 
	# create a file called myfile.txt
	


















HardLink:









## Yum Rpo



















Extending Volume Group:





Extending Volume Group




## Swap Memory

[root@localhost ~]# free -m
[root@localhost ~]# free -m
              total        used        free      shared  buff/cache   available
Mem:            972         461         195          14         315         355
Swap:          2047           0        2047
[root@localhost ~]# lsblk
NAME            MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda               8:0    0   20G  0 disk
├─sda1            8:1    0  300M  0 part /boot
├─sda2            8:2    0    2G  0 part [SWAP]
└─sda3            8:3    0 17.7G  0 part /
sdb               8:16   0    3G  0 disk
└─vg_v1-lv_mylv 253:0    0  6.5G  0 lvm
sdc               8:32   0    2G  0 disk
└─vg_v1-lv_mylv 253:0    0  6.5G  0 lvm
sdd               8:48   0    2G  0 disk
└─vg_v1-lv_mylv 253:0    0  6.5G  0 lvm
sde               8:64   0    2G  0 disk
sr0              11:0    1  4.4G  0 rom
[root@localhost ~]# mkswap /dev/sde
Setting up swapspace version 1, size = 2097148 KiB
no label, UUID=5ce3c15e-4841-4d90-a860-ce9bc06573f8
[root@localhost ~]# free -m
              total        used        free      shared  buff/cache   available
Mem:            972         459         196          14         315         357
Swap:          2047           0        2047
[root@localhost ~]# swapo
swapoff  swapon
[root@localhost ~]# swapon  -a /dev/sde
[root@localhost ~]# free -m
              total        used        free      shared  buff/cache   available
Mem:            972         460         195          14         315         355
Swap:          4095           0        4095
[root@localhost ~]# cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       2097148 0       -2
/dev/sde                                partition       2097148 0       -3
[root@localhost ~]# swapoff /dev/sde
[root@localhost ~]# free -m
              total        used        free      shared  buff/cache   available
Mem:            972         460         195          14         316         355
Swap:          2047           0        2047
[root@localhost ~]# seq 10000000 > myfile.txt
[root@localhost ~]# ls -lh myfile.txt
-rw-r--r--. 1 root root 76M Jun 30 02:28 myfile.txt
[root@localhost ~]# seq 10000000 > myfile.txt^C
[root@localhost ~]# seq 100000000 > myfile.txt
^C
[root@localhost ~]# ls -lh myfile.txt
-rw-r--r--. 1 root root 482M Jun 30 02:28 myfile.txt
[root@localhost ~]# mkswap myfile.txt
Setting up swapspace version 1, size = 493528 KiB
no label, UUID=9b5e88cd-f6f3-4793-ae1f-0759220c4830
[root@localhost ~]# swapon -a myfile.txt
swapon: /root/myfile.txt: insecure permissions 0644, 0600 suggested.
[root@localhost ~]# chmod 600 /root/myfile.txt
[root@localhost ~]# swapon -a myfile.txt
swapon: myfile.txt: swapon failed: Device or resource busy
[root@localhost ~]# free m
              total        used        free      shared  buff/cache   available
Mem:         995676      472504       65868       15164      457304      360204
Swap:       2590676           0     2590676
[root@localhost ~]# free -m
              total        used        free      shared  buff/cache   available
Mem:            972         461          64          14         446         352
Swap:          2529           0        2529
[root@localhost ~]#


### FSTAB ENTRY ###
/dev/sde        swap    swap    defaults 0 0



GREP Command


[root@localhost ~]# cat myfile.tst
cat
dog
concatenate
dogma
category
educated
boondoggle
vindication
chilidog
[root@localhost ~]# cat myfile.tst  |grep dog
dog
dogma
boondoggle
chilidog
[root@localhost ~]# cat myfile.tst  |grep -i dog
dog
dogma
boondoggle
chilidog
[root@localhost ~]# vim myfile.tst
[root@localhost ~]# cat myfile.tst  |grep -i dog
dog
dogma
boondoggle
chilidog
DOG
DoG
[root@localhost ~]# cat myfile.tst  |grep -v dog
cat
concatenate
category
educated
vindication
DOG
DoG
CAT
CaT
[root@localhost ~]# cat myfile.tst  |grep -vi dog
cat
concatenate
category
educated
vindication
CAT
CaT
[root@localhost ~]# cat myfile.tst
[root@localhost ~]# cat myfile.tst
cat
dog
concatenate
dogma
category
educated
boondoggle
vindication
chilidog
DOG
DoG
CAT
CaT
[root@localhost ~]# cat myfile.tst |grep educated -A 2
educated
boondoggle
vindication
[root@localhost ~]# cat myfile.tst |grep educated -B 2
dogma
category
educated
[root@localhost ~]# cat myfile.tst |grep educated -A
grep: option requires an argument -- 'A'
Usage: grep [OPTION]... PATTERN [FILE]...
Try 'grep --help' for more information.
[root@localhost ~]# cat myfile.tst |grep educated -A 1
educated
boondoggle
[root@localhost ~]# cat myfile.tst |grep educated -A1
educated
boondoggle
[root@localhost ~]# grep -e "chilidog|category" myfile.tst
[root@localhost ~]# egrep  "chilidog|category" myfile.tst
category
chilidog
[root@localhost ~]# grep -e "chilid^C|category" myfile.tst
[root@localhost ~]# grep -e "chilidog" -e "boondoggle" myfile.tst
boondoggle
chilidog
[root@localhost ~]# grep -e "chilidog" -e "boondoggle" myfile.tst ^C
[root@localhost ~]# cat myfile.tst
cat
dog
concatenate
dogma
category
educated
boondoggle
vindication
chilidog
DOG
DoG
CAT
CaT
[root@localhost ~]# cat myfile.tst |grep ^cat
cat
category
[root@localhost ~]# cat myfile.tst |grep -i ^cat
cat
category
CAT
CaT
[root@localhost ~]# cat myfile.tst |grep -i dog$
dog
chilidog
DOG
DoG
[root@localhost ~]#




CronJob:







In the above picture, the asterisks refers the specific blocks of time.
To display the contents of the crontab file of the currently logged in user:
$ crontab -l
To edit the current user's cron jobs, do:
$ crontab -e
If it is the first time, you will be asked to choose an editor to edit the cron jobs.

crontab file
In this file, you need to add your cron jobs one by one.
To edit the crontab of a different user, for example ostechnix, do:
$ crontab -u ostechnix -e
1.1. Cron Jobs tutorial
Here is the list of most commonly used cron job commands with examples.
1. To run a cron job at every minute, the format should be like below.
* * * * * <command-to-execute>
For example if the time is 10:00, the next job will run at 10:01, 10:02, 10:03 and so on.
2. To run cron job at every 5th minute, add the following in your crontab file.
*/5 * * * * <command-to-execute>
For example if the time is 10:00, the next job will run at 10:05, 10:10, 10:15 and so on.
3. To run a cron job at every quarter hour (i.e every 15th minute), add this:
*/15 * * * * <command-to-execute>
For example if the time is 10:00, the next job will run at 10:15, 10:30, 10:45 and so on.
4. To run a cron job every hour at minute 30:
30 * * * * <command-to-execute>
For example if the time is 10:00, the next job will run at 10:30, 11:30, 12:30 and so on.
5. You can also define multiple time intervals separated by commas. For example, the following cron job will run three times every hour, at minute 0, 5 and 10:
0,5,10 * * * * <command-to-execute>
6. Run a cron job every half hour i.e at every 30th minute:
*/30 * * * * <command-to-execute>
For example if the time is now 10:00, the next job will run at 10:30, 11:00, 11:30 and so on.
7. Run a job every hour (at minute 0):
0 * * * * <command-to-execute>
For example if the time is now 10:00, the next job will run at 11:00, 12:00, 13:00 and so on.
8. Run a job every 2 hours:
0 */2 * * * <command-to-execute>
For example if the time is now 10:00, the next job will run at 12:00.
9. Run a job every day (It will run at 00:00):
0 0 * * * <command-to-execute>
10. Run a job every day at 3am:
0 3 * * * <command-to-execute>
11. Run a job every Sunday:
0 0 * * SUN <command-to-execute>
Or,
0 0 * * 0 <command-to-execute>
It will run at exactly at 00:00 on Sunday.
12. Run a job on every day-of-week from Monday through Friday i.e every weekday:
0 0 * * 1-5 <command-to-execute>
The job will start at 00:00.
13. Run a job every month (i.e at 00:00 on day-of-month 1):
0 0 1 * * <command-to-execute>
14. Run a job at 16:15 on day-of-month 1:
15 16 1 * * <command-to-execute>
15. Run a job at every quarter i.e on day-of-month 1 in every 3rd month:
0 0 1 */3 * <command-to-execute>
16. Run a job on a specific month at a specific time:
5 0 * 4 * <command-to-execute>
The job will start at 00:05 in April.
17. Run a job every 6 months:
0 0 1 */6 * <command-to-execute>
This cron job will start at 00:00 on day-of-month 1 in every 6th month.
18. Run a job every year:
0 0 1 1 * <command-to-execute>
This cron job will start at 00:00 on day-of-month 1 in January.
We can also use the following strings to define a cron job.







Nice Priorities:

Renice






Nice:



Renice using top command

Press 'r' to renice the pid's















![image](https://user-images.githubusercontent.com/87597729/177003900-ed9e1c9e-f4df-4344-8929-b4e6ef67d01b.png)
