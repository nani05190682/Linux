Apache: It’s a webserver

Required Packages : httpd
Port : http 80, https 443
Configuration file : /etc/httpd/conf/httpd.conf
Service & Daemons : httpd





Default Webhosting Path:




IP based Virtual Hosting:

Reference file:
/usr/share/doc/httpd-2.4.6/httpd-vhosts.conf



<VirtualHost 192.168.96.135:80>


    ServerAdmin webmaster@server.devops.com

    
    DocumentRoot "/var/www/user1/"

    
    ServerName server.devops.com

    
    ServerAlias www.devops.com.

    
    ErrorLog "/var/log/httpd/ipbased1-error_log"

    
    CustomLog "/var/log/httpd/ipbased1-access_log" common

    
</VirtualHost>



Create Configuration file



Create index.html 




				Access the webpage from your webserver:






Name Based Virtual Hosting:










![image](https://github.com/nani05190682/Linux/assets/87597729/42231745-173d-45b7-9d11-14f8d63632c7)
