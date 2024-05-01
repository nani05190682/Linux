
**Lab Exercise 1: Basic Directory Navigation**

**Objective:** To navigate through directories using basic commands.

1. Navigate to the root directory.
2. List the contents of the root directory.
3. Navigate to the `/etc` directory.
4. List the contents of the `/etc` directory.
5. Navigate to your home directory.
6. List the contents of your home directory.

**Solution:**

1. `cd /`
2. `ls`
3. `cd /etc`
4. `ls`
5. `cd ~` or `cd`
6. `ls`

**Lab Exercise 2: Relative Path Navigation**

**Objective:** To navigate through directories using relative paths.

1. Navigate to the `/usr` directory using a relative path.
2. List the contents of the `/usr` directory.
3. Navigate back to your home directory using a relative path.
4. List the contents of your home directory.

**Solution:**

1. `cd ../usr`
2. `ls`
3. `cd ~` or `cd`
4. `ls`

**Lab Exercise 3: Absolute Path Navigation**

**Objective:** To navigate through directories using absolute paths.

1. Navigate to the `/var/log` directory using an absolute path.
2. List the contents of the `/var/log` directory.
3. Navigate back to the root directory using an absolute path.
4. List the contents of the root directory.

**Solution:**

1. `cd /var/log`
2. `ls`
3. `cd /`
4. `ls`

**Lab Exercise 4: Listing Hidden Files**

**Objective:** To list hidden files in a directory.

1. Navigate to your home directory.
2. List all files, including hidden ones.
3. List only the hidden files.
4. List all files using a long listing format.

**Solution:**

1. `cd ~` or `cd`
2. `ls -a`
3. `ls -a | grep "^\."`
4. `ls -l`

**Lab Exercise 5: Creating and Navigating Directories**

**Objective:** To create and navigate directories.

1. Create a directory named `lab_exercises`.
2. Navigate into the `lab_exercises` directory.
3. Create three subdirectories named `ex1`, `ex2`, and `ex3`.
4. Navigate into the `ex1` directory.
5. Navigate back to the `lab_exercises` directory.
6. List the contents of the `lab_exercises` directory.

**Solution:**

1. `mkdir lab_exercises`
2. `cd lab_exercises`
3. `mkdir ex1 ex2 ex3`
4. `cd ex1`
5. `cd ..` or `cd ../`
6. `ls`

**Lab Exercise 6: Moving and Copying Files**

**Objective:** To move and copy files between directories.

1. Create a file named `file1.txt` in `ex1` directory.
2. Copy `file1.txt` to the `ex2` directory.
3. Move `file1.txt` to the `ex3` directory.
4. List the contents of each directory to verify the file movements.

**Solution:**

1. `touch ex1/file1.txt`
2. `cp ex1/file1.txt ex2/`
3. `mv ex1/file1.txt ex3/`
4. `ls ex1`, `ls ex2`, `ls ex3`

**Lab Exercise 7: Removing Files and Directories**

**Objective:** To remove files and directories.

1. Remove `file1.txt` from the `ex2` directory.
2. Remove the `ex3` directory and its contents.
3. List the contents of each directory to verify the removals.

**Solution:**

1. `rm ex2/file1.txt`
2. `rm -r ex3`
3. `ls ex2`, `ls ex3`

**Lab Exercise 8: Using Wildcards**

**Objective:** To use wildcards for file manipulation.

1. Create files named `text1.txt`, `text2.txt`, `data1.csv`, and `data2.csv` in the `ex1` directory.
2. List all files in the `ex1` directory with the extension `.txt`.
3. List all files in the `ex1` directory with names starting with `data`.

**Solution:**

1. `touch ex1/text1.txt ex1/text2.txt ex1/data1.csv ex1/data2.csv`
2. `ls ex1/*.txt`
3. `ls ex1/data*`

**Lab Exercise 9: Displaying Directory Structure**

**Objective:** To display the directory structure.

1. Display the current directory structure using the `tree` command.
2. Display the directory structure of the root directory using the `tree` command.
3. Display the directory structure of the `/etc` directory using the `tree` command.

**Solution:**

1. `tree`
2. `tree /`
3. `tree /etc`

**Lab Exercise 10: Finding Files**

**Objective:** To find files using the `find` command.

1. Find all files named `example.txt` in the `/home` directory.
2. Find all files with the `.log` extension in the `/var/log` directory.
3. Find all directories named `test` in the root directory.

**Solution:**

1. `find /home -name "example.txt"`
2. `find /var/log -name "*.log"`
3. `find / -type d -name "test"`

