### php Laravel application deployment on Ubuntu VPS
Prerequisite
- Apache2 Server
- NodeJS
- PHP (Latest version)
- MySQL (Latest version)
- PhpMyAdmin/MySQL Workbench
- Composer (Latest version)

[NodeJS Install](https://nodejs.org/en/download/prebuilt-binaries/current)
```bash
cd /opt/
wget https://nodejs.org/dist/v20.12.2/node-v20.12.2-linux-x64.tar.xz
tar xf node-v20.12.2-linux-x64.tar.xz
nano ~/.bashrc
NODEJS=/opt/node-v20
PATH=$PATH:$HOME/bin:$NODEJS/bin
export PATH
source ~/.bashrc
node -v & npm -v
```

[Apache2 Install](https://httpd.apache.org/)
```bash
apt update
apt install apache2
systemctl status apache2
```

Apache HTTP Server setups to enable PHP support
```bash
apt install libapache2-mod-php
systemctl restart apache2
cd /var/www/html
touch php-version.php
<?php
   phpinfo()
?>
crtl + x & y
Your server IP/php-version.php
php -v
```

[MySQL Server Install](https://ubuntu.com/server/docs/install-and-configure-a-mysql-server)
```bash
apt install mysql-server
apt install mysql-client
apt install php8.1-mysql
apt install php8.1-curl
sudo ss -tap | grep mysql # The network status of the MySQL service
service mysql status
service mysql restart
sudo mysql_secure_installation
mysql or mysql -u root -p
SELECT user, host FROM mysql.user;
show databases;
CREATE USER 'root'@'localhost' IDENTIFIED BY 'Sql@054003'; # if exist then
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Sql@054003';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION; # or
GRANT ALL PRIVILEGES ON YourDatabase.* TO 'root'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```
```bash
sudo systemctl restart mysql
```
```bash
mysql -u root -p
SHOW GRANTS FOR 'root'@'localhost';
```

[PhpMyAdmin Install](https://www.phpmyadmin.net/)
```bash
apt install phpmyadmin
# clicked on enter not select any option
```