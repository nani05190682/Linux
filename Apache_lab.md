
---

### LAB Exercise 1: Set Up a Self-Signed SSL Certificate for Apache

**Objective:** Configure Apache with a self-signed SSL certificate to secure web traffic.

**Tasks:**
1. Install the necessary software packages.
2. Generate a self-signed SSL certificate.
3. Configure Apache to use the self-signed certificate.

**Solution:**

1. Install required packages:

    ```bash
    sudo dnf install mod_ssl openssl httpd -y
    ```

2. Generate a self-signed SSL certificate:

    ```bash
    openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/pki/tls/private/selfsigned.key -out /etc/pki/tls/certs/selfsigned.crt
    ```

3. Edit the SSL configuration file:

    ```bash
    sudo nano /etc/httpd/conf.d/ssl.conf
    ```

    Update the paths:
    ```
    SSLCertificateFile /etc/pki/tls/certs/selfsigned.crt
    SSLCertificateKeyFile /etc/pki/tls/private/selfsigned.key
    ```

4. Restart Apache:

    ```bash
    sudo systemctl restart httpd
    ```

---

### LAB Exercise 2: Set Up a Virtual Host with SSL

**Objective:** Create an SSL-enabled virtual host on Apache.

**Tasks:**
1. Create a directory to host the web files.
2. Configure a virtual host with SSL enabled.
3. Test the setup by accessing the virtual host over HTTPS.

**Solution:**

1. Create a web directory:

    ```bash
    sudo mkdir /var/www/vhost1
    echo "Welcome to VHost1 over SSL!" | sudo tee /var/www/vhost1/index.html
    ```

2. Create an SSL-enabled virtual host:

    ```bash
    sudo nano /etc/httpd/conf.d/vhost1_ssl.conf
    ```

    Add:
    ```
    <VirtualHost *:443>
        ServerAdmin webmaster@vhost1.local
        DocumentRoot /var/www/vhost1
        ServerName vhost1.local

        SSLEngine on
        SSLCertificateFile /etc/pki/tls/certs/selfsigned.crt
        SSLCertificateKeyFile /etc/pki/tls/private/selfsigned.key

        ErrorLog /var/log/httpd/vhost1_error.log
        CustomLog /var/log/httpd/vhost1_access.log combined
    </VirtualHost>
    ```

3. Restart Apache and test:

    ```bash
    sudo systemctl restart httpd
    ```

    Access via: `https://vhost1.local`

---

### LAB Exercise 3: Force HTTP Traffic to HTTPS

**Objective:** Ensure all web traffic to your Apache server is encrypted by redirecting HTTP traffic to HTTPS.

**Tasks:**
1. Configure your default virtual host to redirect all traffic to HTTPS.
2. Test by accessing your website using the HTTP protocol.

**Solution:**

1. Edit the default configuration or create a new one:

    ```bash
    sudo nano /etc/httpd/conf.d/redirect_to_ssl.conf
    ```

    Add:
    ```
    <VirtualHost *:80>
        ServerName your_server_domain_or_IP
        Redirect permanent / https://your_server_domain_or_IP/
    </VirtualHost>
    ```

    Replace `your_server_domain_or_IP` with your domain or IP address.

2. Restart Apache:

    ```bash
    sudo systemctl restart httpd
    ```

3. Test by accessing the website using `http://` - it should automatically redirect to `https://`.

---

