
---

### LAB Exercise: Setting Up Name-Based Virtual Hosting in Apache

**Objective:** Set up two websites on a single Apache server using Name-Based Virtual Hosting. Each website should be accessible using a unique domain name.

**Requirements:**

- A CentOS 8 machine.
- Apache installed.

**Tasks:**
1. Install the necessary software packages.
2. Create directories for two websites: `site1.local` and `site2.local`.
3. Create a virtual host configuration for each site.
4. Update your `/etc/hosts` file for local resolution (if testing locally).
5. Test both websites to ensure they load correctly.

---

**Solution:**

1. **Install Apache:**

    ```bash
    sudo dnf install httpd -y
    ```

2. **Create web directories for the two sites:**

    ```bash
    sudo mkdir /var/www/site1.local
    sudo mkdir /var/www/site2.local
    ```

    Add sample index pages to each:

    ```bash
    echo "Welcome to Site1!" | sudo tee /var/www/site1.local/index.html
    echo "Welcome to Site2!" | sudo tee /var/www/site2.local/index.html
    ```

3. **Configure virtual hosts:**

    Create a new configuration file:

    ```bash
    sudo nano /etc/httpd/conf.d/vhosts.conf
    ```

    Add the following configurations:

    ```
    <VirtualHost *:80>
        ServerAdmin webmaster@site1.local
        DocumentRoot /var/www/site1.local
        ServerName site1.local
        ErrorLog /var/log/httpd/site1_error.log
        CustomLog /var/log/httpd/site1_access.log combined
    </VirtualHost>

    <VirtualHost *:80>
        ServerAdmin webmaster@site2.local
        DocumentRoot /var/www/site2.local
        ServerName site2.local
        ErrorLog /var/log/httpd/site2_error.log
        CustomLog /var/log/httpd/site2_access.log combined
    </VirtualHost>
    ```

4. **Update `/etc/hosts` for local resolution** (if testing on the same machine without actual DNS setup):

    ```bash
    sudo nano /etc/hosts
    ```

    Add:

    ```
    127.0.0.1   site1.local
    127.0.0.1   site2.local
    ```

5. **Restart Apache and test the setup:**

    ```bash
    sudo systemctl start httpd
    ```

    In a web browser or using `curl`, check:

    ```
    http://site1.local
    http://site2.local
    ```

    Each URL should show the welcome message for the respective site.

---

