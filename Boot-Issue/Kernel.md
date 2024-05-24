To reinstall a crashed kernel from the boot menu on RHEL 8, follow these steps:

1. **Reboot the System**: Start by rebooting the RHEL 8 system.

2. **Access GRUB Menu**: During the boot process, when the GRUB menu appears, press any key to interrupt the normal boot process and enter the GRUB menu.

3. **Select Kernel Entry**: Select the kernel entry you want to reinstall (usually the latest functional kernel) and press the `e` key to edit it.

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

8. **Reinstall Kernel Package**: Use `dnf` to reinstall the kernel package. First, list the available kernels to find the correct package name:

   ```bash
   dnf list kernel
   ```

   Identify the crashed kernel package from the list, and then reinstall it using:

   ```bash
   dnf reinstall <kernel-package-name>
   ```

   Replace `<kernel-package-name>` with the actual name of the kernel package.

9. **Regenerate GRUB Configuration**: Regenerate the GRUB configuration to ensure the new kernel is recognized:

   ```bash
   grub2-mkconfig -o /boot/grub2/grub.cfg
   ```

10. **Exit and Reboot**: Exit the chroot environment and reboot the system:

    ```bash
    exit
    reboot
    ```

After rebooting, the system should boot with the reinstalled kernel. If the kernel was causing issues due to corruption or other problems, reinstalling it may resolve those issues.
