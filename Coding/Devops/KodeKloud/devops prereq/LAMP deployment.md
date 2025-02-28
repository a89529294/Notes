
OS: CentOS
## install firewall
- `sudo yum install firewalld`
- `sudo systemctl start firewalld`
- `sudo systemctl enable firewalld`

## install mariadb (community fork of mysql)
- `sudo yum install mariadb-server`
- `sudo vi /etc/my.cnf` # configure the file with the right port, or keep the default 3306
- `sudo systemctl start mariadb`
- `sudo systemctl enable mariadb`

## configure firewall
- `sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp`
- `sudo firewall-cmd --reload`
- `sudo firewall-cmd --list-all`
- (this step is not necessary if php app and db is on the same server)

## configure db (db and php on same server)
- `sudo mysql` to enter mysql shell
- `CREATE DATABASE ecomdb;`
- `CREATE USER 'ecomuser'@'localhost' IDENTIFIED BY 'ecompassword';`
- `GRANT ALL PRIVILEGES ON *.* TO 'ecomuser'@'localhost';`
- `FLUSH PRIVILEGES;`
- `exit` exit from mariadb shell

## load data
- `mysql < db-load-script.sqp`
- `mysql`
- `show databases;`
- `use ecomdb;`
- `SELECT * FROM products;` to make sure the script loaded

## install httpd, php
- `sudo yum install httpd php php-mysqlnd`

## configure firewall
- `sudo firewall-cmd --permanent --zone=public --add-port=80/tcp`
- `sudo firewall-cmd --reload`

## configure httpd
- `sudo vi /etc/httpd/conf/httpd.conf`, configure DirectoryIndex to use index.php instead of index.html

## start httpd
- `sudo systemctl start httpd`
- `sudo systemctl enable httpd`

## download code
- `git clone xxxxx /var/www/html`
- update index.php to use right db address, name and credentials

## test
- `curl http://localhost`

## if php app and db are on two different servers
- `$link = mysqli_connect('127.20.0.101, username,pw)` on php side
- on mariadb server, run `mysql` to enter shell
	- `CREATAE DAATABASE ecomdb;`
	- `CREATE USER 'ecomuser'@'127.20.0.102' IDENTIFIED BY 'ecompassword';`
	- `GRANT ALL PRIVILEGES ON *.* TO 'ecomuser'@'127.20.0.102';`
	- `FLUSH PRIVILEGES;`