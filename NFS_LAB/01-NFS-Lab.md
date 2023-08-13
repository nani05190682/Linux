Sure, here are four lab exercises with solutions for CentOS NFS:

**Lab Exercise 1: Configuring NFS Server**

In this lab exercise, you will configure an NFS server on a CentOS machine.

1. Install the NFS server package on your CentOS machine using the following command:

   ```
   sudo yum install nfs-utils
   ```

2. Create a directory to share using NFS:

   ```
   sudo mkdir /nfs_share
   ```

3. Edit the /etc/exports file to allow access to the directory:

   ```
   sudo nano /etc/exports
   ```

   Add the following line to the file:

   ```
   /nfs_share *(rw,sync,no_subtree_check)
   ```

4. Restart the NFS server:

   ```
   sudo systemctl restart nfs-server
   ```

**Solution:**

To verify that the NFS server is running, you can use the following command:

```
sudo systemctl status nfs-server
```

You should see a message indicating that the service is active and running.

To test the NFS share, you can mount it on another CentOS machine using the following command:

```
sudo mount <nfs_server_ip>:/nfs_share /mnt
```

Replace `<nfs_server_ip>` with the IP address of your NFS server.

You should now be able to access the contents of the NFS share by navigating to the /mnt directory on the client machine.

**Lab Exercise 2: Configuring NFS Client**

In this lab exercise, you will configure an NFS client on a CentOS machine.

1. Install the NFS client package on your CentOS machine using the following command:

   ```
   sudo yum install nfs-utils
   ```

2. Create a directory to mount the NFS share:

   ```
   sudo mkdir /mnt/nfs_share
   ```

3. Mount the NFS share using the following command:

   ```
   sudo mount <nfs_server_ip>:/nfs_share /mnt/nfs_share
   ```

   Replace `<nfs_server_ip>` with the IP address of your NFS server.

4. Verify that the NFS share is mounted:

   ```
   df -h
   ```

**Solution:**

To verify that the NFS share is mounted, you can use the following command:

```
df -h
```

You should see …[omitted]
