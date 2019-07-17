# server

#### IP address
```
165.227.93.12
```
#### ssh port
```
2200
```
#### Project URL
```
http://165.227.93.12/
```
#### ssh command
```
ssh grader@165.227.93.12 -p 2200 -i path/to/privateKey
```
#### Software Installed
1. apache2
2. python2.7
4. libapache2-mod-wsgi-py
5. python-dev
6. flask
7. sqlalchemy
8. flask_json
9. virtualenv
#### Apache Configuration
```
<VirtualHost *:80>
     # Add machine's IP address (use ifconfig command)
     ServerName 165.227.93.12
     # Give an alias to to start your website url with
     WSGIDaemonProcess catalog python-path=/var/www/catalog:/var/www/catalog/catalog/venv/lib/python2.7/site-packages user=www-data group=www-data
     WSGIProcessGroup catalog
     WSGIScriptAlias / /var/www/catalog/catalog.wsgi
     <Directory /var/www/catalog/catalog/>
     # set permissions as per apache2.conf file
            WSGIScriptReloading On
            WSGIApplicationGroup %{GLOBAL}
            Options FollowSymLinks
            AllowOverride None
            Require all granted
     </Directory>
     Alias /static /var/www/catalog/catalog/static
     <Directory /var/www/catalog/catalog/static/>
         Order allow,deny
         Allow from all
     </Directory>

     ErrorLog ${APACHE_LOG_DIR}/error.log
     LogLevel warn
     CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
