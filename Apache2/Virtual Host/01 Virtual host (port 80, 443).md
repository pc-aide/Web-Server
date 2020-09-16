#01 Virtual host (port 80, 443).md

## Updates
````bash
apt update
apt upgrade
````

## Install Web server
````bash
apt install -y apache2
````

## systemctl
````bash
systemctl enable apache2
````

## Enable SSL
````bash
a2enmod ssl
systemctl restart apache2
````

## Create keys (openSSl)
````bash
openssl genrsa -out /etc/ssl/certs/siteB.key 2048
openssl req -new -key /etc/ssl/certs/siteB.key -out /etc/ssl/certs/siteB.csr
CA
QC
QC
PC-Aide
IT
siteB.com
help@pc-aide.com
````

## Private key
````bash
openssl x509 -req -days 365 -in /etc/ssl/certs/siteB.csr -signkey /etc/ssl/certs/siteB.key -out /etc/ssl/certs/siteB.crt
````

## Create folders
````bash
mkdir /var/www/site{A,B}
````

## /etc/apache2/sites-enable/000-default.conf
````Virtual host
<VirtualHost *:80>
        ServerName siteA.com
        ServerAlias www.siteA.com
        DocumentRoot /var/www/siteA
</VirtualHost>

# SSL Redirect
<VirtualHost *:80>
        ServerName siteB.com
        ServerAlias www.siteB.com
        Redirect permanent / https://siteB.com
</VirtualHost>

<VirtualHost *:443>
        ServerName siteB.com
        ServerAlias www.siteB.com
        DocumentRoot /var/www/siteB
        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/siteB.crt
        SSLCertificateKeyFile /etc/ssl/certs/siteB.key
</VirtualHost>
````

## Reload
````bash
systemctl reload apache2
````
