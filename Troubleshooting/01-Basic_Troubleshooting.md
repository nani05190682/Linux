Troubleshooting with `systemd` on RHEL 8 involves a variety of tools and commands to diagnose and resolve issues.

### Basic `systemd` Commands

1. **Check the Status of a Service**
   ```bash
   systemctl status <service_name>
   ```
   Example:
   ```bash
   systemctl status httpd
   ```

2. **Start, Stop, and Restart Services**
   ```bash
   systemctl start <service_name>
   systemctl stop <service_name>
   systemctl restart <service_name>
   ```

3. **Enable and Disable Services**
   ```bash
   systemctl enable <service_name>
   systemctl disable <service_name>
   ```

4. **View Logs**
   ```bash
   journalctl -u <service_name>
   ```
   Example:
   ```bash
   journalctl -u httpd
   ```

### Analyzing Boot Issues

1. **View Boot Logs**
   ```bash
   journalctl -b
   ```

2. **View Logs from the Previous Boot**
   ```bash
   journalctl -b -1
   ```

3. **Check the Overall System Status**
   ```bash
   systemctl list-units --state=failed
   ```

### Managing Journal Logs

1. **View All Logs**
   ```bash
   journalctl
   ```

2. **Filter Logs by Time**
   ```bash
   journalctl --since "YYYY-MM-DD HH:MM:SS"
   journalctl --since "2 hours ago"
   ```

3. **View Kernel Logs**
   ```bash
   journalctl -k
   ```

### Common Troubleshooting Scenarios

1. **Service Not Starting**
   - Check the service status:
     ```bash
     systemctl status <service_name>
     ```
   - View detailed logs:
     ```bash
     journalctl -xe
     ```

2. **Unit File Issues**
   - Verify the unit file syntax:
     ```bash
     systemd-analyze verify /etc/systemd/system/<service_name>.service
     ```

3. **Slow Boot Times**
   - Analyze boot performance:
     ```bash
     systemd-analyze blame
     systemd-analyze critical-chain
     ```

### Advanced Diagnostics

1. **Debugging a Service**
   - Start the service in debug mode:
     ```bash
     systemctl start <service_name> -v
     ```

2. **Checking Dependencies**
   - List dependencies of a service:
     ```bash
     systemctl list-dependencies <service_name>
     ```

3. **Analyzing System State**
   - Generate a dump of the current system state:
     ```bash
     systemd-cgtop
     systemd-analyze dump
     ```
