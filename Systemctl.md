# systemctl lab-01
1. Query the state of all units to verify a system startup.

         systemctl

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


         $ systemctl list-unit-files --failed --type=service

============================================================================================

# systemctl lab-02 Identify the Status of systemd Units

1.  List all service units on the system.

         [root@serverX ~]$  systemctl list-units --type=service
   
2.  List all socket units, active and inactive, on the system.

         [root@serverX ~]$  systemctl list-units --type=socket --all
    
3. Explore the status of the chronyd service. This service is used for network time synchronization (NTP)

   3.1.  Display the status of the chronyd service. Note the process ID of any active daemon


         [root@serverX ~]$  systemctl status chronyd
         
    3.2. Confirm that the listed daemons are running.


         [student@serverX ~]$ ps -p PID
         
 4. Explore the status of the sshd service. This service is used for secure encrypted communication between systems.
 
    4.1. Determine if the sshd service is enabled to start at system boot


         [root@serverX ~]$  systemctl is-enabled sshd
         
    4.2. Determine if the sshd service is active without displaying all of the status information


         [student@serverX ~]$ sudo systemctl is-active sshd
         
         
    4.3. Display the status of the sshd service.


         [root@serverX ~]$  systemctl status sshd
         
 5. List the enabled or disabled states of all service units.
 
         [root@serverX ~]$  systemctl list-unit-files --type=service

    
     


         
    
  
 

