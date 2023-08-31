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

That's it! You have successfully set up NFS on CentOS 8. You can now proceed with testing and performing any additional configurations or tasks as required.

