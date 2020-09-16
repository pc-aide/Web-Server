#01 Virtual host (port 80, 443).md

## Updates
apt update
apt upgrade

## Install Web server
apt install -y apache2

## systemctl
systemctl enable apache2

## Enable SSL
a2enmod ssl
systemctl restart apache2

## Create keys (openSSl)
openssl genrsa -out /etc/ssl/certs/siteB.key 2048
openssl req -new -key /etc/ssl/certs/siteB.key -out /etc/ssl/certs/siteB.csr
CA
QC
QC
PC-Aide
IT
siteB.com
help@pc-aide.com

## Private key
openssl x509 -req -days 365 -in /etc/ssl/certs/siteB.csr -signkey /etc/ssl/certs/siteB.key -out /etc/ssl/certs/siteB.crt

## Create folders
mkdir /var/www/site{A,B}

## /etc/apache2/sites-enable/000-default.conf
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

## Reload
systemctl reload apache2
