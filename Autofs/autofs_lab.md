Automount in CentOS 8 uses the `autofs` service to automatically mount filesystems when they are accessed and unmount them after a period of inactivity. Here are the lab exercises focused on `autofs`:

### **Lab Exercise 1: Basic Automount of an NFS Share**

**Objective**: Automatically mount an NFS share when accessed.

**Steps**:
1. Ensure NFS server is set up and a share is available. (Assuming a share at `<NFS_SERVER_IP>:/srv/nfs`)

2. Install the `autofs` package:
   ```bash
   sudo dnf install -y autofs
   ```

3. Edit `/etc/auto.master` and add:
   ```bash
   /mnt/nfs /etc/auto.nfs
   ```

4. Create `/etc/auto.nfs` with the content:
   ```bash
   nfs_share -fstype=nfs <NFS_SERVER_IP>:/srv/nfs
   ```

5. Restart `autofs`:
   ```bash
   sudo systemctl restart autofs
   ```

6. Access the directory to see if it auto mounts:
   ```bash
   ls /mnt/nfs/nfs_share
   ```

**Expected Outcome**: The directory should automatically mount and show the contents of the NFS share.

---

### **Lab Exercise 2: Automount a Local Disk Partition**

**Objective**: Automatically mount a local disk partition when accessed.

**Steps**:
1. Let's assume there's an extra disk `/dev/sdb1` that you wish to automount.

2. Install the `autofs` package if not already:
   ```bash
   sudo dnf install -y autofs
   ```

3. Edit `/etc/auto.master` and add:
   ```bash
   /mnt/disk /etc/auto.disk
   ```

4. Create `/etc/auto.disk` with the content:
   ```bash
   local -fstype=ext4 :/dev/sdb1
   ```

5. Restart `autofs`:
   ```bash
   sudo systemctl restart autofs
   ```

6. Access the directory to see if it auto mounts:
   ```bash
   ls /mnt/disk/local
   ```

**Expected Outcome**: The directory should automatically mount and show the contents of the disk partition.

---

### **Lab Exercise 3: Set an Automount Timeout**

**Objective**: Customize the automount timeout.

**Steps**:
1. Using the configuration from either Exercise 1 or 2, modify the `/etc/auto.master` file.

2. For the mount point you're focusing on (e.g., `/mnt/nfs`), set a timeout of 60 seconds:
   ```bash
   /mnt/nfs /etc/auto.nfs --timeout=60
   ```

3. Restart `autofs`:
   ```bash
   sudo systemctl restart autofs
   ```

4. Access the directory to ensure it mounts:
   ```bash
   ls /mnt/nfs/nfs_share  # or /mnt/disk/local based on which exercise you're following
   ```

5. Wait for more than 60 seconds and then check the mount status:
   ```bash
   mount | grep /mnt/nfs/nfs_share
   ```

**Expected Outcome**: After waiting for 60 seconds, the mount should automatically be unmounted due to inactivity.

---

For each exercise, ensure you've set up any required prerequisites (e.g., an NFS server for Exercise 1). Make sure to test thoroughly and ensure your configuration works as expected.
