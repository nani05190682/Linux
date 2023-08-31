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




