Sure, here are 5 lab exercises for Linux File/Directory Permissions with solutions:

## Exercise 1: Basic Permissions

1. Create a file named `test.txt` in your home directory.
2. Set the file permissions so that the owner can read and write to the file, and everyone else has no permissions.
3. Verify the permissions using the `ls -l` command.

**Solution:**

```bash
1. touch ~/test.txt
2. chmod 600 ~/test.txt
3. ls -l ~/test.txt
```

## Exercise 2: Changing Ownership

1. Create a directory named `mydir` in your home directory.
2. Change the ownership of the directory to another user on the system.
3. Verify the ownership using the `ls -l` command.

**Solution:**

```bash
1. mkdir ~/mydir
2. sudo chown otheruser ~/mydir
3. ls -l ~/mydir
```

## Exercise 3: Advanced Permissions

1. Create a file named `secret.txt` in your home directory.
2. Set the file permissions so that the owner can read and write to the file, and the group has read-only access.
3. Add another user to the group and verify that they can read the file.

**Solution:**

```bash
1. touch ~/secret.txt
2. chmod 640 ~/secret.txt
3. sudo usermod -a -G groupname otheruser
   su otheruser
   cat ~/secret.txt
```

## Exercise 4: Sticky Bit

1. Create a directory named `shared` in the root directory.
2. Set the permissions on the directory so that anyone can create files in it, but only the owner can delete them.
3. Verify that the sticky bit is set on the directory.

**Solution:**

```bash
1. sudo mkdir /shared
2. sudo chmod 1777 /shared
3. ls -ld /shared
```

## Exercise 5: Special Permissions

1. Create a file named `executable.sh` in your home directory.
2. Set the file permissions so that it is executable by anyone, but can only be run by the owner.
3. Verify that the special permission is set on the file.

**Solution:**

```bash
1. touch ~/executable.sh
2. chmod 711 ~/executable.sh
3. ls -l ~/executable.sh
```


02 Lab
---

### **Lab Exercise 1: Understanding Basic Permissions**

**Objective:** Understand and list the basic permissions of files and directories.

**Tasks:**

1. Navigate to your home directory.
2. Create a file named `testfile.txt` and a directory named `testdir`.
3. List the permissions of both `testfile.txt` and `testdir`.

**Solution:**

1. `cd ~`
2. `touch testfile.txt`
   `mkdir testdir`
3. `ls -l testfile.txt testdir`

### **Lab Exercise 2: Modifying File Permissions**

**Objective:** Change file permissions using the `chmod` command.

**Tasks:**

1. Make `testfile.txt` executable for the user.
2. Remove the write permission for the group and others on `testfile.txt`.
3. Verify your changes.

**Solution:**

1. `chmod u+x testfile.txt`
2. `chmod go-w testfile.txt`
3. `ls -l testfile.txt`

### **Lab Exercise 3: Directory Permissions**

**Objective:** Understand the implications of directory permissions.

**Tasks:**

1. Remove the execute permission for the user on `testdir`.
2. Try to change into the `testdir`.
3. Restore the execute permission and verify you can access it.

**Solution:**

1. `chmod u-x testdir`
2. `cd testdir` (This will give an error since execute permission is needed to change into a directory)
3. `chmod u+x testdir`
   `cd testdir` (This should now work)

### **Lab Exercise 4: Recursive Permission Change**

**Objective:** Change permissions recursively on directories and files.

**Tasks:**

1. Inside `testdir`, create two sub-directories `subdir1` and `subdir2` and a file named `innerfile.txt`.
2. Recursively give full permissions to user, group, and others on `testdir` and verify.

**Solution:**

1. `cd testdir`
   `mkdir subdir1 subdir2`
   `touch innerfile.txt`
2. `chmod -R 777 .`
   `ls -l` and `ls -l *` (This will display permissions for the directory and its contents)

### **Lab Exercise 5: Using Symbolic Permissions**

**Objective:** Use symbolic representations with `chmod` to adjust permissions.

**Tasks:**

1. Add read and execute permissions to `testfile.txt` for the group.
2. Remove write permissions for others on `testfile.txt`.
3. Set the user's permissions on `testfile.txt` to read and write only.
4. Verify your changes.

**Solution:**

1. `chmod g+rx testfile.txt`
2. `chmod o-w testfile.txt`
3. `chmod u=rw testfile.txt`
4. `ls -l testfile.txt`

---

