# systemctl lab
1. Query the state of all units to verify a system startup.

$ systemctl

2. Query the state of only the service units

   [root@serverX ~]# systemctl --type=service
   
3. Investigate any units which are in a failed or maintenance state. Optionally, add the -l option to show the full output.


   [root@serverX ~]# systemctl status rngd.service -l

4. The status argument may also be used to determine if a particular unit is active and show if the unit is enabled to start at boot time. Alternate commands can also easily show the active and enabled states:


    [root@serverX ~]# systemctl is-active sshd
    [root@serverX ~]# systemctl is-enabled sshd

5. List the active state of all loaded units. Optionally, limit the type of unit. The --all option will add inactive units.


    [root@serverX ~]# systemctl list-units --type=service
    [root@serverX ~]# systemctl list-units --type=service --all
    
    
 6. View the enabled and disabled settings for all units. Optionally, limit the type of unit.


   [root@serverX ~]# systemctl list-unit-files --type=service
   
 7. View only failed services


   [root@serverX ~]# systemctl --failed --type=service
