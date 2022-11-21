**Deployment** in the context of this book is preparing the web application for use.

# Stages of deployment
1. *Server provisioning*: process of setting up infrastructure and essential software.
	- installing an operating system
	- configuring networking
	- preparing SSH
2. *Configuration management*: configure the already provisioned servers to a specific state that can support the application at hand.
	- application dependencies
	- NGINX configuration
	- PostgreSQL pg_hba.conf
	- firewall setting
3. *Application deployment*: Its simplest form is most likely copying files over SFTP.


