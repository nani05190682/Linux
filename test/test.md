### Lab Exercise: Managing Linux File Permissions

**Objective:**
The goal of this lab exercise is to understand and practice managing file and directory permissions in Linux. You will learn how to view, modify, and interpret file and directory permissions using `chmod`, `chown`, and `chgrp`.

---

#### Prerequisites:
- Basic understanding of Linux terminal commands.
- Access to a Linux system (physical or virtual).


https://miro.medium.com/v2/resize:fit:666/1*-T25a5h_HF54jCYVlXKxHA@2x.png![Uploading image.png…]()


---

### Part 1: Understanding File Permissions

1. **Check the current permissions:**
   - Run the following command to list the permissions of files in your current directory:
     ```bash
     ls -l
     ```
   - Observe the output. The permissions are displayed in the following format:  
     `-rwxr-xr--`  
     The first character indicates the file type (e.g., `-` for regular file, `d` for directory), and the next nine characters show the permissions for the owner, group, and others.

2. **Interpret the permission format:**
   - Example: `-rwxr-xr--`
     - **Owner** (`rwx`): The owner has read, write, and execute permissions.
     - **Group** (`r-x`): The group has read and execute permissions.
     - **Others** (`r--`): Others have read-only permission.

---

### Part 2: Changing File Permissions with `chmod`

1. **Create a new file:**
   ```bash
   touch myfile.txt
   ```
   - Check its permissions:
     ```bash
     ls -l myfile.txt
     ```

2. **Modify permissions:**
   - Grant read, write, and execute permissions to the owner:
     ```bash
     chmod u+rwx myfile.txt
     ```
   - Revoke write permission for the group:
     ```bash
     chmod g-w myfile.txt
     ```
   - Remove all permissions for others:
     ```bash
     chmod o-rwx myfile.txt
     ```
   - Check the updated permissions:
     ```bash
     ls -l myfile.txt
     ```

3. **Using numeric mode:**
   - Change the permissions to `rwxr-xr--` using the numeric mode:
     ```bash
     chmod 754 myfile.txt
     ```
   - Verify the change:
     ```bash
     ls -l myfile.txt
     ```

---

### Part 3: Changing Ownership with `chown` and `chgrp`

1. **Check current ownership:**
   - Run the following command to check the owner and group of the file:
     ```bash
     ls -l myfile.txt
     ```

2. **Change file ownership:**
   - Change the owner of the file to a user (replace `newuser` with an actual username):
     ```bash
     sudo chown newuser myfile.txt
     ```

3. **Change group ownership:**
   - Change the group of the file to a different group (replace `newgroup` with an actual group name):
     ```bash
     sudo chgrp newgroup myfile.txt
     ```
   - Verify the changes:
     ```bash
     ls -l myfile.txt
     ```

---

### Part 4: Special Permissions (Setuid, Setgid, Sticky Bit)

1. **Setuid (User ID on execution):**
   - Grant setuid permission on a file:
     ```bash
     sudo chmod u+s myfile.txt
     ```
   - Check the permissions (notice the `s` in the owner section):
     ```bash
     ls -l myfile.txt
     ```

2. **Setgid (Group ID on execution):**
   - Grant setgid permission on a directory:
     ```bash
     mkdir mydir
     sudo chmod g+s mydir
     ```
   - Verify the permissions of the directory:
     ```bash
     ls -ld mydir
     ```

3. **Sticky bit (For directories):**
   - Grant the sticky bit on a directory (useful for shared directories like `/tmp`):
     ```bash
     sudo chmod +t mydir
     ```
   - Verify the sticky bit (`t` at the end of the permissions):
     ```bash
     ls -ld mydir
     ```

---

### Part 5: Practice Scenarios

1. **Scenario 1: Create a Shared Directory**
   - Create a directory called `shared` where users can create files, but only the file owner can delete them.
     ```bash
     mkdir shared
     sudo chmod 1777 shared
     ```

2. **Scenario 2: Secure a File**
   - Create a file `secret.txt` that only the owner can read and write.
     ```bash
     touch secret.txt
     chmod 600 secret.txt
     ```

3. **Scenario 3: Team Collaboration**
   - Create a directory `project` where the group can read, write, and execute, but others have no access.
     ```bash
     mkdir project
     chmod 770 project
     ```

---

### Part 6: Clean Up

- Remove all created files and directories:
  ```bash
  rm myfile.txt
  rm -r mydir shared project secret.txt
  ```

---
