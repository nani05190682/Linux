**Lab Exercise: File Management in Linux**

**Objective:**
The objective of this lab exercise is to familiarize students with creating, viewing, and removing files in a Linux environment using command-line tools.

**Prerequisites:**
- Basic understanding of the Linux terminal.
- Access to a Linux system or a virtual machine running a Linux distribution.

**Instructions:**

**Part 1: Creating Files**

1. Open a terminal window on your Linux system.
2. Navigate to the directory where you want to create the files for this exercise.
3. Use the `touch` command to create the following files:
   - File1.txt
   - File2.txt
   - File3.txt
4. Verify that the files have been created by listing the contents of the current directory using the `ls` command.

**Part 2: Viewing Files**

1. Use the `cat` command to view the contents of File1.txt. Take note of what is displayed in the terminal.
2. Use the `echo` command to add some text to File2.txt. For example:
   ```
   echo "Hello, world!" > File2.txt
   ```
3. Use the `cat` command again to view the contents of File2.txt and verify that the text you added is displayed.
4. Use the `less` command to view the contents of File3.txt. Navigate through the file using the arrow keys. Press `q` to exit `less` when done.

**Part 3: Removing Files**

1. Use the `rm` command to remove File3.txt.
2. Verify that File3.txt has been removed by listing the contents of the current directory using the `ls` command.
3. Use the `rm` command with the `-i` option to interactively remove File1.txt. Follow the prompts to confirm the deletion.
4. Verify that File1.txt has been removed by listing the contents of the current directory using the `ls` command.

**Bonus Challenge:**

- Use the `mkdir` command to create a new directory within the current directory.
- Create a new file inside the newly created directory using any method of your choice.
- Remove the directory and its contents using the `rm` command with the `-r` (recursive) option.

**Solutions:**

**Part 1: Creating Files**
```
touch File1.txt File2.txt File3.txt
ls
```

**Part 2: Viewing Files**
```
cat File1.txt
echo "Hello, world!" > File2.txt
cat File2.txt
less File3.txt
```

**Part 3: Removing Files**
```
rm File3.txt
ls
rm -i File1.txt
ls
```

**Bonus Challenge:**
```
mkdir NewDirectory
touch NewDirectory/NewFile.txt
rm -r NewDirectory
```


