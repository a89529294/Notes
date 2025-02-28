- go to [centos download](https://www.centos.org/download/) and select arm64 iso
- open virtualbox
	- iso image, select the one just downloaded
	- type: linux
	- subType: oracle linux
	- version: oracle linux (arm 64bit)

## network access prereq
- check vm instance if ssh is open
- `sudo systemctl status sshd`
	- if ssh is not running, 
	- `sudo systemctl start sshd`
	- `sudo systemctl enable sshd`
	- if ssh is not installed 
		- `sudo yum update -y`
		- `sudo yum install openssh-server -y`
		- `sudo systemctl start sshd`
		- `sudo systemctl enable sshd`
		- `sudo firewall-cmd --permanent --add-service=ssh`
		- `sudo firewall-cmd --reload`
		- `sudo firewall-cmd --list-services`
		- finally check `sudo systemctl status sshd`
## network access

- open virtualbox
- right click on vm instance and choose settings, under expert -> network, click on port forwarding, then add a new rule
	- name: SSH PORT
	- host port: 2222
	- guest port: 22
- then on host machine, `ssh username@127.0.0.1 -p 2222`, then enter password