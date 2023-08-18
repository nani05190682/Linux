
---

### LAB Exercise: Setting Up IP-Based Virtual Hosting in Apache

**Objective:** Host two websites on a single Apache server using IP-Based Virtual Hosting. Each website should be accessible using a unique IP address.

**Requirements:**

- A CentOS 8 machine with at least two IP addresses configured.
- Apache installed.

**Tasks:**
1. Install the necessary software packages.
2. Configure the server to listen on both IP addresses.
3. Create directories for two websites, one for each IP address.
4. Set up IP-based virtual host configurations for each site.
5. Test both websites to ensure they load correctly.

---

**Solution:**

1. **Install Apache:**

    ```bash
    sudo dnf install httpd -y
    ```

2. **Configure Apache to Listen on Both IPs:**

    Edit the main configuration:

    ```bash
    sudo nano /etc/httpd/conf/httpd.conf
    ```

    Ensure there's a line to make Apache listen on both IP addresses:

    ```
    Listen [IP1]:80
    Listen [IP2]:80
    ```

    Replace `[IP1]` and `[IP2]` with your actual IP addresses.

3. **Create web directories for the two sites:**

    ```bash
    sudo mkdir /var/www/site-ip1
    sudo mkdir /var/www/site-ip2
    ```

    Add sample index pages to each:

    ```bash
    echo "Welcome to Site IP1!" | sudo tee /var/www/site-ip1/index.html
    echo "Welcome to Site IP2!" | sudo tee /var/www/site-ip2/index.html
    ```

4. **Configure IP-based virtual hosts:**

    Create a new configuration file:

    ```bash
    sudo nano /etc/httpd/conf.d/ip_vhosts.conf
    ```

    Add the following configurations:

    ```
    <VirtualHost [IP1]:80>
        DocumentRoot /var/www/site-ip1
        ServerName servername1.example.com
        ErrorLog /var/log/httpd/site-ip1_error.log
        CustomLog /var/log/httpd/site-ip1_access.log combined
    </VirtualHost>

    <VirtualHost [IP2]:80>
        DocumentRoot /var/www/site-ip2
        ServerName servername2.example.com
        ErrorLog /var/log/httpd/site-ip2_error.log
        CustomLog /var/log/httpd/site-ip2_access.log combined
    </VirtualHost>
    ```

    Replace `[IP1]` and `[IP2]` with your actual IP addresses.

5. **Restart Apache and test the setup:**

    ```bash
    sudo systemctl restart httpd
    ```

    In a web browser or using `curl`, check:

    ```
    http://[IP1]
    http://[IP2]
    ```

    Each IP should load the welcome message for the respective site.

---

