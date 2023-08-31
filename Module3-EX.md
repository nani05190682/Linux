NFS
---

Sure, here's a lab exercise for NFS on CentOS 8:

## Lab Exercise: Setting up NFS on CentOS 8

### Objective
In this lab exercise, you will learn how to set up a Network File System (NFS) server and client on CentOS 8.

### Prerequisites
- Two CentOS 8 virtual machines (VMs) with network connectivity
- Root access to both VMs

### Instructions
1. On the first VM, install the NFS server package:
   ```
   sudo dnf install nfs-utils
   ```

2. Configure the NFS server by editing the `/etc/exports` file. Add the necessary configuration to export a directory of your choice.

3. Export the NFS share by running the appropriate command.

4. Start the NFS server and enable it to start automatically at boot time.

5. On the second VM, install the NFS client package:
   ```
   sudo dnf install nfs-utils
   ```

6. Create a mount point for the NFS share.

7. Mount the NFS share on the second VM using the appropriate command.

8. Verify that the NFS share is successfully mounted on the second VM.




Autofs
---

**Lab Exercise: Setting Up and Configuring `autofs`**

### Objective:

The primary objective of this lab is to help you understand, set up, and configure `autofs` on a Linux system. By the end of this lab exercise, you should be able to automatically mount and unmount file systems without manual intervention.

### Prerequisites:

1. A Linux system with root access.
2. Basic understanding of Linux file systems and mount command.

### Scenario:

You are the system administrator for a software development company. Developers often need to access project data stored on various NFS servers. Instead of having these NFS mounts permanently reside in the `/etc/fstab` file, you decide to use `autofs` to automatically mount them when accessed and unmount them when not in use, saving system resources.

### Tasks:

1. **Installation**:
   - Install the `autofs` package using the package manager for your Linux distribution.

2. **Configuration**:
   - Configure `autofs` to use the `/misc` directory as its mount point.
   - Ensure that the `autofs` service starts automatically at boot time.

3. **NFS Server Setup** (Hypothetical for the purpose of this exercise):
   - Assume there are two NFS servers available: `nfs-server1` and `nfs-server2`.
   - `nfs-server1` shares a directory `/data/projectA` and `nfs-server2` shares a directory `/data/projectB`.

4. **Auto.master File Configuration**:
   - Update the `/etc/auto.master` file to include the mount point `/misc` and its associated map file.

5. **Auto.misc Map File Configuration**:
   - Create or update the `/etc/auto.misc` map file.
   - Configure it so that when a user accesses `/misc/projectA`, it mounts the NFS share from `nfs-server1` (`/data/projectA`) and when a user accesses `/misc/projectB`, it mounts the NFS share from `nfs-server2` (`/data/projectB`).

6. **Service Restart and Testing**:
   - Restart the `autofs` service to apply your changes.
   - Test the configuration by accessing the `/misc/projectA` and `/misc/projectB` directories. Ensure that the correct shares are mounted automatically.
   - Verify that the mounts are automatically unmounted after a period of inactivity.

7. **Troubleshooting**:
   - Check the status of the `autofs` service.
   - Investigate any relevant logs for errors or warnings.
   - Ensure that the NFS servers are accessible and the shared directories exist.

8. **Additional Task (Advanced)**:
   - Create a timeout of 3 minutes for the NFS mounts, after which, if not accessed, they should be unmounted.

### Tips:

- Remember to check syntax and ensure that there are no typos in configuration files.
- Use tools like `mount`, `systemctl`, and `cat` to verify your configurations.
- Always back up original configuration files before making changes.



**Lab Exercise: Configuring DNS on RHEL8**

### Objective:

The primary goal of this lab is to guide you through the process of setting up a DNS (Domain Name System) server on a RHEL8 system. By the end of this exercise, you should be able to set up and manage a local DNS server and serve domain requests for a mock company.

### Prerequisites:

1. A system running RHEL8 with root access.
2. Basic knowledge of Linux, networking, and domain concepts.


DNS
---

### Scenario:

You are the system administrator for a startup named "TechPioneers." Your company has decided to set up an internal DNS server for managing domain requests for `techpioneers.local`. The main web application server for your company resides at the IP address `192.168.0.10`.

### Tasks:

1. **Installation**:
   - Install the necessary packages to set up a BIND DNS server on RHEL8.

2. **Main Configuration**:
   - Modify the main BIND configuration file to allow queries from local network clients.
   - Ensure that BIND is set up to run in a chroot environment for added security.

3. **Zone File Configuration**:
   - Set up a forward lookup zone for `techpioneers.local`.
   - Define an A record for `app.techpioneers.local` pointing to `192.168.0.10`.
   - Set up a reverse lookup zone for `192.168.0.0/24` and ensure the PTR record for `192.168.0.10` points back to `app.techpioneers.local`.

4. **Testing**:
   - Start the BIND service and ensure it's set to start on boot.
   - Use the `dig` and `nslookup` utilities from a client machine or the server itself to query the DNS server for the `app.techpioneers.local` domain.
   - Test the reverse lookup as well to confirm the PTR record's functionality.

5. **DNS Client Configuration**:
   - Configure a client machine to use the newly set up DNS server. Adjust its resolver configuration appropriately.
   - Ensure the client machine can resolve `app.techpioneers.local` using the DNS server.

6. **Firewall Configuration**:
   - Modify the system firewall rules to allow DNS queries to the server.
   - Test from a client machine to ensure that the firewall rules permit DNS queries.

7. **Logs and Troubleshooting**:
   - Familiarize yourself with the location and format of the BIND logs.
   - Simulate or identify a couple of common DNS-related issues (like a misconfigured zone file) and practice troubleshooting them using the logs.

8. **Advanced Task (Optional)**:
   - Set up a secondary (slave) DNS server for redundancy. Ensure that zone transfers between the primary and secondary servers are functioning correctly.

### Tips:

- BIND configuration files are sensitive to syntax and formatting. Always verify configurations using appropriate tools before restarting the service.
- Remember that changes in DNS records might be cached. You might need to flush DNS cache or wait for the TTL (Time To Live) to expire for changes to take effect.
- Using tools like `named-checkconf` and `named-checkzone` can help validate BIND configuration and zone files, respectively.

### Conclusion:

Upon successful completion of this lab exercise, you should have a functional DNS server set up on RHEL8, capable of serving domain requests for the internal domain `techpioneers.local`. This foundation is crucial for network and system administrators managing enterprise environments.


POstfix
---

**Lab Exercise: Configuring Postfix Mail Server on RHEL8**

### Objective:

The primary goal of this lab is to guide you through the process of setting up a basic Postfix mail server on RHEL8. By the end of this exercise, you should be able to send and receive emails locally and understand the essential configurations related to Postfix.

### Prerequisites:

1. A system running RHEL8 with root access.
2. Basic knowledge of Linux administration and networking.

### Scenario:

You are the IT administrator for a growing startup named "InnovateTech." The company has decided to run its internal mail server for communications among team members. Your task is to set up and configure a basic Postfix mail server for the domain `innovatetech.local`.

### Tasks:

1. **Installation**:
   - Install the necessary packages required to set up the Postfix mail server and mail utilities on RHEL8.

2. **Postfix Configuration**:
   - Modify the main Postfix configuration file to:
     - Set the mail domain to `innovatetech.local`.
     - Define the mailbox location.
     - Specify the trusted networks.
     - Ensure proper hostname resolution.
   - Make any other necessary modifications to ensure mail delivery to local mailboxes.

3. **Testing Local Mail Delivery**:
   - Use the `mail` command or similar utilities to send emails between local users on the Postfix server.
   - Verify that the users can read the sent emails.

4. **Aliases and Forwarding**:
   - Set up an alias for a user, for instance, redirect mails sent to `support@innovatetech.local` to a specific user's mailbox.
   - Test the alias configuration by sending an email to the alias and confirming its redirection.

5. **Firewall Configuration**:
   - Adjust the system firewall rules to allow inbound and outbound SMTP traffic.
   - Test by attempting to send an email to the server from an external source (if applicable).

6. **Log Monitoring and Troubleshooting**:
   - Familiarize yourself with the location and format of the Postfix logs.
   - Identify some common mail delivery issues and practice troubleshooting them using the logs.

7. **Security (Advanced Task)**:
   - Set up and configure basic spam filtering mechanisms.
   - Implement basic security features to harden your Postfix installation, such as limiting the number of recipients per message or rate-limiting outbound emails.

8. **Additional Task (Optional)**:
   - Set up a basic mail client (like `mutt`) on a separate machine to connect to the Postfix server. Configure it to send and receive emails using the Postfix server.

### Tips:

- Always verify Postfix configurations using appropriate tools or test methods before finalizing any setup.
- Remember to monitor the mail queue (`mailq` command) regularly and understand how to manage it.
- Be cautious when adjusting security settings; over-restricting can lead to legitimate emails being blocked, while under-restricting can make the server vulnerable to misuse.

### Conclusion:

Upon successful completion of this lab exercise, you should have a functional Postfix mail server set up on RHEL8, capable of handling basic email operations for the domain `innovatetech.local`. This foundation is pivotal for IT professionals managing communications in business environments.


Samba
---

**Lab Exercise: Configuring a Samba Server on CentOS 8**

### Objective:

The main aim of this lab is to guide you through the setup and configuration of a basic Samba server on CentOS 8. By the conclusion of this exercise, you should be capable of creating and managing Samba shares accessible by Windows clients in a local network.

### Prerequisites:

1. A system running CentOS 8 with root or sudo access.
2. Basic familiarity with Linux administration, networking, and file permissions.

### Scenario:

You're the lead system administrator for a design agency named "DesignMasters." Your team frequently collaborates using graphical assets that are stored locally. To ensure seamless access to these assets across Linux and Windows workstations, you've been tasked with setting up a Samba share named "assets" on a CentOS 8 server.

### Tasks:

1. **Installation**:
   - Install the necessary packages required to set up a Samba server on CentOS 8.

2. **Samba Configuration**:
   - Create a directory named `assets` in `/srv/samba/`.
   - Modify the Samba configuration file to:
     - Define a new share named `assets`.
     - Allow read and write access for the design team.
     - Ensure that guests can view the contents but cannot modify them.
     - Assign the appropriate directory path for the share.

3. **User and Group Management**:
   - Create a group named `designers`.
   - Add some test users to this group.
   - Ensure these users have Samba access by setting up Samba passwords for them.

4. **Directory Permissions**:
   - Adjust the file system permissions on the `assets` directory to:
     - Allow full access to the `designers` group.
     - Ensure others can read the directory but not write to it.

5. **Firewall Configuration**:
   - Modify the firewall settings to allow Samba traffic through.

6. **Service Management**:
   - Start the Samba services and ensure they are set to start on boot.

7. **Testing the Configuration**:
   - From a Linux workstation:
     - Use `smbclient` or a file manager to access the Samba share and test file operations.
   - From a Windows workstation:
     - Map the network drive using the Samba server's IP address and the share name.
     - Test the share by creating, modifying, and deleting files.
     - Confirm that guest access can view files but not alter them.

8. **Security and Advanced Configuration (Optional)**:
   - Set up encrypted connections for the Samba shares.
   - Implement logging for the Samba server to monitor user activities.
   - Use SELinux to further secure your Samba installation.

### Tips:

- Always back up the original configuration files before making changes.
- Use the `testparm` utility to verify your Samba configuration.
- Monitor the Samba logs for any errors or warnings that may indicate configuration issues.

### Conclusion:

Upon successful completion of this lab exercise, you should have a functional Samba server on CentOS 8 that serves as a bridge between Linux and Windows workstations in a multi-platform work environment. This capability is invaluable for system administrators working in diverse IT settings.
