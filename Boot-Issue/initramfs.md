To reinstall a crashed initramfs from the boot menu on RHEL 8, follow these steps:

1. **Reboot the System**: Start by rebooting the RHEL 8 system.

2. **Access GRUB Menu**: During the boot process, when the GRUB menu appears, press any key to interrupt the normal boot process and enter the GRUB menu.

3. **Select Kernel Entry**: Select the kernel entry you want to use to reinstall the initramfs (usually the latest functional kernel) and press the `e` key to edit it.

4. **Edit Kernel Parameters**: In the editing mode, navigate to the line starting with `linux` or `linux16`, which specifies the kernel parameters. Append `rd.break enforcing=0` to the end of this line. This instructs the system to enter a special mode with a root shell before the system fully boots.

5. **Boot with Changes**: Press `Ctrl + x` or `F10` to boot with the modified kernel parameters.

6. **Remount the File System**: After the system boots into emergency mode with a root shell, the root file system is mounted as read-only. Remount it with read-write permissions using the following command:

   ```bash
   mount -o remount,rw /sysroot
   ```

7. **Change Root**: Change the root to the mounted file system:

   ```bash
   chroot /sysroot
   ```

8. **Recreate initramfs**: Use `dracut` to recreate the initramfs. First, remove the existing initramfs:

   ```bash
   rm -f /boot/initramfs-<kernel-version>.img
   ```

   Replace `<kernel-version>` with the version of the kernel for which you want to recreate the initramfs.

   Then, regenerate the initramfs for the kernel:

   ```bash
   dracut /boot/initramfs-<kernel-version>.img <kernel-version>
   ```

   Again, replace `<kernel-version>` with the appropriate kernel version.

9. **Exit and Reboot**: Exit the chroot environment and reboot the system:

    ```bash
    exit
    reboot
    ```

After rebooting, the system should boot with the newly recreated initramfs for the selected kernel. This process can help resolve issues related to a corrupted or malfunctioning initramfs.
