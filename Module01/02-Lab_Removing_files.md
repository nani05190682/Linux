**Lab Exercise: Removing Files and Directories in Linux**

**Objective:**
The objective of this lab exercise is to practice removing files and directories in a Linux environment using command-line tools.

**Prerequisites:**
- Basic understanding of the Linux terminal.
- Access to a Linux system or a virtual machine running a Linux distribution.

**Instructions:**

**Part 1: Removing Files**

1. Open a terminal window on your Linux system.
2. Navigate to the directory where you want to perform the file removal for this exercise.
3. Use the `touch` command to create a few sample files. For example:
   ```
   touch file1.txt file2.txt file3.txt
   ```
4. List the contents of the directory to verify that the files have been created using the `ls` command.
5. Use the `rm` command to remove one of the files. For example:
   ```
   rm file1.txt
   ```
6. Verify that the file has been removed by listing the contents of the directory again using the `ls` command.

**Part 2: Removing Directories**

1. Create a new directory within the current directory using the `mkdir` command. For example:
   ```
   mkdir test_directory
   ```
2. List the contents of the directory to verify that the new directory has been created.
3. Navigate into the newly created directory using the `cd` command.
4. Create some sample files inside the directory using the `touch` command. For example:
   ```
   touch file4.txt file5.txt
   ```
5. Navigate back to the parent directory using `cd ..`.
6. Use the `rmdir` command to remove the directory. Note that `rmdir` can only remove empty directories. For example:
   ```
   rmdir test_directory
   ```
7. Verify that the directory has been removed by listing the contents of the directory again using the `ls` command.

**Bonus Challenge:**

- Create a directory structure with nested directories and files.
- Use the `rm` command with the `-r` (recursive) option to remove the entire directory structure.

**Solutions:**

**Part 1: Removing Files**
```
touch file1.txt file2.txt file3.txt
ls
rm file1.txt
ls
```

**Part 2: Removing Directories**
```
mkdir test_directory
ls
cd test_directory
touch file4.txt file5.txt
cd ..
rmdir test_directory
ls
```

**Bonus Challenge:**
```
mkdir -p nested_directory/sub_directory
touch nested_directory/file6.txt
touch nested_directory/sub_directory/file7.txt
rm -r nested_directory
ls
```
