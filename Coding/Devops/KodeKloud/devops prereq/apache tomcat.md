- Tomcat is a **full-fledged Java web server and servlet container**. It is specifically designed to run Java-based web applications, including Servlets, JavaServer Pages (JSP), and other Java EE (now Jakarta EE) components.
- It provides built-in support for handling HTTP requests, managing sessions, and serving dynamic content through JSP or other Java-based templating engines.
- Tomcat is a complete solution for Java web applications, requiring no additional frameworks to function as a web server (though frameworks like Spring can be added for enhanced functionality).

## download and installation

### installing java
1. check if java is installed `java -version`, if its is you are done. Otherwise to step 2.
2. 
```bash
-uname m # check architecture, arm64 or x64
cat /etc/*release* # check os

# if os is rpm package based, e.g., Red Hat Enterprise Linux, CentOS, Oracle Linux, Fedora)
# two options are available,  
# one that ends with .rpm
# one that ends with .tar.gz
# maker sure they are of the right architecture

# on any linux os you can also just download the one that ends with .tar.gz with the right architecture

# summary: check architecture, then check if it is rpm based. if it is, yuo can use the one that ends with .rpm or .tar.gz. If it is not, you can use the one that ends with .deb or .tar.gz
```
3. based on if you choose to download (.rpm) or (.tar.gz) installation will be different:
	1. rpm: `wget https://download.oracle.com/java/23/latest/jdk-23_linux-x64_bin.rpm` then `sudo rpm -ivh jdk-23_linux-x64_bin.rpm`. Verify installation `java -version`
	2. tar.gz: `wget https://download.oracle.com/java/23/latest/jdk-23_linux-x64_bin.tar.gz`, then `tar -xzf jdk-23_linux-x64_bin.tar.gz` then `sudo mv jdk-23 /opt/`, then `vi ~/.bashrc` then `export JAVA_HOME=/opt/jdk-23` and `export PATH=$JAVA_HOME/bin:$PATH`. Finally `source ~/.bashrc` and `java -version`

### installing apache tomcat
1. `wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.36/bin/apache-tomcat-10.1.36.tar.gz`
2. `tar -xvzf apache-tomcat-10.1.36.tar.gz`
3. `./apache-tomcat-10.1.36/bin/startup.sh`
4. Open your browser and navigate to `http://localhost:8080`. You should see the Tomcat welcome page.

### make tomcat a service
1. the following assumes you moved tomcat to `/opt/tomcat`
2. `sudo vi /etc/systemd/system/tomcat.service`
3.  add the following to the newly created file
   ```bash
[Unit]
Description=Apache Tomcat Web Application Container
After=syslog.target network.target

[Service]
Type=forking

# Set environment variables
Environment=JAVA_HOME=/usr/lib/jvm/java-11-openjdk (or your Java path)
Environment=CATALINA_HOME=/opt/tomcat (or your tomcat path)
Environment=CATALINA_BASE=/opt/tomcat
Environment=CATALINA_PID=/opt/tomcat/temp/tomcat.pid

# Set the user and group to run Tomcat
User=tomcat
Group=tomcat

# ExecStart and ExecStop commands
ExecStart=/opt/tomcat/bin/startup.sh (or your tomcat path)
ExecStop=/opt/tomcat/bin/shutdown.sh

# Restart on failure
RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target
```
4. create a new user just to run tomcat `sudo useradd -r -s /bin/false tomcat` and `sudo chown -R tomcat:tomcat /opt/tomcat`
5. `sudo systemctl daemon-reload`

#### tomcat as a service commands
- `sudo systemctl start tomcat`
- `sudo systemctl enable tomcat`
- `sudo systemctl status tomcat`
- `sudo systemctl stop tomcat`
- `sudo systemctl restart tomcat`
- `sudo journalctl -u tomcat` view logs

#### what does the tomcat user do?
When you run `sudo systemctl start tomcat`, `systemd` reads the `tomcat.service` file and starts Tomcat using the `tomcat` user.

You don't need to manually switch to the `tomcat` user or use `sudo -u tomcat` because `systemd` handles this for you.

You would only need to switch to the `tomcat` user if you're **manually running Tomcat scripts** (e.g., `startup.sh` or `shutdown.sh`) without using `systemctl`. For example: `sudo -u tomcat /opt/tomcat/bin/startup.sh`

## Deploying on tomcat
tomcat/
├── bin/       (scripts for starting/stopping Tomcat)
├── conf/      (configuration files)
├── lib/       (shared libraries)
├── logs/      (log files)
├── webapps/   (directory for deploying web applications)
├── work/      (temporary working files)
└── temp/      (temporary files)

- `cp myapp.war /path/to/tomcat/webapps/`
- go to `http://localhost:8080/myapp/` to verify or visit the logs `tail -n 10 /opt/tomcat/logs/catalina.out`