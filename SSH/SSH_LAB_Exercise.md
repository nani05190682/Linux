### Lab Exercise 1: Basic SSH Installation and Configuration

**Objective**: Set up an SSH server, connect to it from a client machine, and customize the welcome banner.

1. Install the OpenSSH server package on CentOS 8.
2. Start and enable the SSH service.
3. Connect from a client machine to the server using the `ssh` command.
4. Modify the server configuration to display a custom banner upon login.
5. Restart the SSH service and reconnect from the client to observe the new banner.

### Lab Exercise 2: Changing the Default SSH Port

**Objective**: Configure the SSH server to run on a non-default port and adjust the firewall rules to allow connections on this new port.

1. Edit the SSH configuration to change the default port (22) to another value (e.g., 2222).
2. Adjust the `firewalld` rules to permit traffic on this new port.
3. Restart the SSH service.
4. Attempt to connect using SSH from a client, specifying the new port.

### Lab Exercise 3: SSH Key-Based Authentication

**Objective**: Set up passwordless SSH login between a client machine and the CentOS 8 server.

1. On the client machine, generate an SSH key pair.
2. Copy the public key to the CentOS 8 server using `ssh-copy-id`.
3. Disable password authentication for SSH on the server.
4. Restart the SSH service on the server.
5. From the client, connect to the server using SSH key authentication.





### Solutions
---


### Solution for Lab Exercise 1: Basic SSH Installation and Configuration

1. Install the OpenSSH server package:
   ```bash
   sudo dnf install openssh-server
   ```

2. Start and enable the SSH service:
   ```bash
   sudo systemctl start sshd
   sudo systemctl enable sshd
   ```

3. From a client machine, connect using:
   ```bash
   ssh username@server_ip
   ```

4. Modify the SSH configuration to set a custom banner:
   ```bash
   echo "Welcome to the SSH server!" | sudo tee /etc/ssh_banner
   sudo nano /etc/ssh/sshd_config
   ```
   Add or modify the line:
   ```
   Banner /etc/ssh_banner
   ```

5. Restart the service:
   ```bash
   sudo systemctl restart sshd
   ```

### Solution for Lab Exercise 2: Changing the Default SSH Port

1. Edit the SSH configuration:
   ```bash
   sudo nano /etc/ssh/sshd_config
   ```
   Change the line:
   ```
   Port 2222
   ```

2. Adjust firewall rules:
   ```bash
   sudo firewall-cmd --permanent --add-port=2222/tcp
   sudo firewall-cmd --reload
   ```

3. Restart SSH:
   ```bash
   sudo systemctl restart sshd
   ```

4. From the client:
   ```bash
   ssh -p 2222 username@server_ip
   ```

### Solution for Lab Exercise 3: SSH Key-Based Authentication

1. On the client:
   ```bash
   ssh-keygen
   ```

2. Copy the public key to the server:
   ```bash
   ssh-copy-id -p 22 username@server_ip  # use the default port or your custom port
   ```

3. Disable password authentication on the server:
   ```bash
   sudo nano /etc/ssh/sshd_config
   ```
   Change or add:
   ```
   PasswordAuthentication no
   ```

4. Restart SSH:
   ```bash
   sudo systemctl restart sshd
   ```

5. From the client, SSH should now use key authentication.



Allowing root login via SSH on RHEL 9 involves modifying the SSH configuration file to permit root login. While enabling root login is generally discouraged for security reasons, if it's necessary in your environment, you can follow these steps.

### Steps to Allow Root Login via SSH

1. **Edit the SSH Configuration File**
   - Open the `/etc/ssh/sshd_config` file using a text editor:
   ```bash
   sudo vi /etc/ssh/sshd_config
   ```

2. **Locate the PermitRootLogin Directive**
   - Find the line that contains `PermitRootLogin`. It might be commented out (with `#`) or set to `no`:
   ```bash
   #PermitRootLogin no
   ```

3. **Change the PermitRootLogin Setting**
   - Uncomment the line (remove the `#`) and change the value to `yes`:
   ```bash
   PermitRootLogin yes
   ```

4. **Restart the SSH Service**
   - Save the changes and restart the SSH service to apply the new configuration:
   ```bash
   sudo systemctl restart sshd
   ```

5. **Optional: Check Firewall and SELinux**
   - Ensure that SSH is allowed through the firewall (if not already configured):
   ```bash
   sudo firewall-cmd --permanent --add-service=ssh
   sudo firewall-cmd --reload
   ```
   - If SELinux is enforcing policies that prevent root login, you may need to adjust SELinux settings or disable SELinux temporarily:
   ```bash
   sudo setenforce 0
   ```

6. **Login as Root**
   - Now, attempt to log in as root via SSH:
   ```bash
   ssh root@<IP_of_Host>
   ```



To deny a user access via SSH on RHEL 9, you can configure this in the SSH server configuration file (`/etc/ssh/sshd_config`). Below are the methods for denying a user from accessing the system via SSH.

### Method 1: Using `DenyUsers` Directive

1. **Edit the SSH Configuration File**  
   Open the `/etc/ssh/sshd_config` file using a text editor.
   ```bash
   sudo vi /etc/ssh/sshd_config
   ```

2. **Add `DenyUsers` Directive**  
   In the file, add the `DenyUsers` directive followed by the username(s) you want to block.
   ```bash
   DenyUsers username1 username2
   ```
   For example, to deny the user `testuser` from logging in via SSH, you would add:
   ```bash
   DenyUsers testuser
   ```

3. **Restart the SSH Service**  
   After saving the changes, restart the SSH service to apply the configuration.
   ```bash
   sudo systemctl restart sshd



