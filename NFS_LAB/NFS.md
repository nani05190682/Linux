
---

### Exercise 1: Setting up NFS server on CentOS

**Task:** Install and set up an NFS server on CentOS, and export a directory for client access.

**Steps:**
1. Install the necessary NFS server packages:
```bash
sudo yum install -y nfs-utils
```

2. Create a directory to be exported:
```bash
sudo mkdir /nfs_share
```

3. Modify `/etc/exports` to export the directory:
```bash
echo "/nfs_share  *(rw,sync,no_root_squash)" | sudo tee -a /etc/exports
```

4. Start and enable the NFS services:
```bash
sudo systemctl start nfs-server
sudo systemctl enable nfs-server
```

**Solution:** The directory `/nfs_share` should now be accessible from NFS clients. You can verify by checking the exported directories with `showmount -e localhost`.

---

### Exercise 2: Mounting NFS share on a CentOS client

**Task:** Set up a CentOS machine to mount the NFS share you created in the previous exercise.

**Steps:**
1. Install the necessary NFS client packages:
```bash
sudo yum install -y nfs-utils
```

2. Create a directory to mount the NFS share:
```bash
sudo mkdir /mnt/nfs
```

3. Mount the NFS share:
```bash
sudo mount [NFS_SERVER_IP]:/nfs_share /mnt/nfs
```

**Solution:** You should now be able to access the files in `/mnt/nfs` which are actually stored on the NFS server. You can verify by navigating to `/mnt/nfs` and checking its contents.

---

### Exercise 3: Persisting the NFS mount across reboots

**Task:** Ensure that the NFS share is automatically mounted on boot.

**Steps:**
1. Edit the `/etc/fstab` file:
```bash
sudo nano /etc/fstab
```

2. Add the following line at the end of the file:
```
[NFS_SERVER_IP]:/nfs_share /mnt/nfs nfs defaults 0 0
```

**Solution:** After saving the file and rebooting, the NFS share should be automatically mounted to `/mnt/nfs`. You can verify by checking the mounted filesystems with `df -h`.

---

### Exercise 4: Securing NFS exports

**Task:** Modify the NFS export to only be accessible from a specific client IP address and restrict the permissions to read-only.

**Steps:**
1. Edit the `/etc/exports` file on the NFS server:
```bash
sudo nano /etc/exports
```

2. Modify the line related to `/nfs_share` to look like this:
```
/nfs_share  [CLIENT_IP](ro,sync,no_root_squash)
```

3. Restart the NFS server to apply changes:
```bash
sudo systemctl restart nfs-server
```

**Solution:** Only the specific client with the IP address `[CLIENT_IP]` should now be able to access the NFS share, and it should be in read-only mode. You can verify from the client side by trying to write to the mounted directory, which should now be disallowed.

---

