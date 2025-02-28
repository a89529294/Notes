## mysql on centos stream 9

```bash
sudo dnf install https://dev.mysql.com/get/mysql84-community-release-el9-1.noarch.rpm #1
sudo dnf install mysql-community-server #2
sudo systemctl start mysqld #3
```
1. What It Does:
	1. **Downloads the RPM**:  
    - dnf install fetches the file mysql84-community-release-el9-1.noarch.rpm from the URL https://dev.mysql.com/get/.  
    - This RPM isn’t the MySQL server itself—it’s a small package containing repository configuration data.
	2. **Installs the RPM**:  
    - The dnf install command doesn’t just download; it also installs the RPM onto your system.
    - This is similar to what rpm -ivh would do, but dnf handles it smarter by resolving any dependencies (though this specific RPM typically has none).
	3. **Adds MySQL to DNF Packages**:  
    - The installed RPM places a .repo file (e.g., mysql-community.repo) into /etc/yum.repos.d/.
    - This .repo file tells dnf (and yum, its alias) where to find MySQL packages—like a map pointing to MySQL’s official repository servers.
    - Once this is done, dnf knows about the MySQL packages (e.g., mysql-community-server) and can install them from the repo in future commands.
    4. **check dbf repo**:
    - `dnf repolist`
2. What it Does:
	- **Downloads MySQL Community Server**:  
    - dnf looks at the repositories configured on your system, including the MySQL repository you added earlier (via sudo dnf install https://dev.mysql.com/get/mysql84-community-release-el9-1.noarch.rpm).
    - It finds the mysql-community-server package in the MySQL 8.4 community repository (e.g., mysql84-community).
    - It downloads the package files (and any dependencies) to a temporary cache (usually under /var/cache/dnf/).
    - **Installs MySQL Community Server**:  
    - After downloading, dnf installs the mysql-community-server package onto your system.
    - This includes the MySQL server binary (e.g., mysqld), configuration files (e.g., /etc/my.cnf), and related components needed to run the MySQL database server.
    - It sets up the service so you can start it with systemctl.
3. What it Does:
	- Starts the `mysqld` daemon
	- Not to be confused with `mysql` which is the command line client to connect to the server by `mysql -u root -p`, then enter your password

### connection

`mysql -u root -p` then enter password
You can find the temporary password from `cat /var/log/mysqld.log`, `sudo grep 'temporary password' /var/log/mysqld.log`

### change password (after connecting to mysql)

`ALTER USER 'root'@'localhost' IDENTIFIED BY 'my_new_pw';`

### create new user

`CREATE USER 'john'@'localhost' IDENTIFIED BY 'my_new_pw';`

If you wish to allow another user from another machine to access mysql on this machine: `CREATE USER 'john'@'192.168.1.1' IDENTIFIED BY 'my_new_pw'`. Then john on the other machine can do `mysql -u john -p -h 192.168.1.2`. Assuming mysqld is running on 192.168.1.2

`CREATE USER 'john'@'%' IDENTIFIED BY 'my_new_pw';` allows user to connect from any ip.

### Privileges

- syntax: `GRANT <PERMISSION> ON <DB.TABLE> TO 'john'@'localhost';`
- `GRANT SELECT ON school.persons TO 'john'@'localhost';`
- `GRANT ALL PRIVILEGES ON *.* TO 'john'@'localhost';`
- `GRANT SELECT, UPDATE ON school.* TO 'john'@'localhost';`
- `SHOW GRANTS FOR 'john'@'localhost';`

All privileges
- `ALL PRIVILEGES`
- `CREATE`, `CREATE ON *.*` creates db and tables anywhere. `CREATE ON school.*` creates tables in the database school only.
- `DROP`, `DROP ON *.*` drops db and tables anywhere. `DROP ON school.*` drops tables in the database school only.
- `DELETE`, delete rows from table
- `INSERT`, insert rows into table
- `SELECT`, read table
- `UPDATE`, update table
### commands (used in mysql shell, i.e. after connecting to mysql)

- `SHOW DATABASES;`
- `CREATE DATABASE db_name;` create db
- `USE db_name;` switch into a db
- `CREATE TABLE persons(name varchar(255), age int, location varchar(255));`
- `SHOW TABLES;`
- `INSERT INTO persons values("John", 45, "NY");`
- `SELECT * FROM persons;`
### files and directories
#### log
 `/var/log/mysqld.log`

#### config
- /etc/my.cnf
- /etc/mysql/my.cnf
- $MYSQL_HOME/my.cnf
- [datadir]/my.cnf
- ~/.my.cnf
You can verify this by running `mysql --help`
  
#### data
`/var/lib/mysql`

## mongodb on centos stream 9

### installation 

[official docs on installation](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-red-hat/)

1. `sudo vi /etc/yum.repos.d/mongodb-org-8.0.repo`
2.  paste the following in
```
[mongodb-org-8.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/9/mongodb-org/8.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://pgp.mongodb.com/server-8.0.asc
```
3. `sudo dnf install -y mongodb-org`
4. `sudo systemctl start mongod`, `sudo systemctl enable mongod`
5. `sudo systemctl status mongod`

### hierarchy

db -> collection -> document
### files

- `/var/log/mongodb/mongod.log`, can find default port in it.
- `/etc/mongod.conf`, modify host and port here.

### connection

- `mongo` enter mongo shell, by default there is no restriction

### commands

- `show dbs`
- `use my_db`, creates and switch to my_db
- `db` show current db
- `db.createCollection("persons")`
- `show collections`
- `db.persons.insert({"name":"John", "age":11})`
- `db.persons.find()` find all documents in persons collection
- `db.persons.find({"name", "John"})`

