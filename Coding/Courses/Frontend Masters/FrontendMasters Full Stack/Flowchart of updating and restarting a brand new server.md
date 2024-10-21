1. create a droplet on DO
2. configure [ssh](obsidian://open?vault=notes&file=Coding%2FCourses%2FFrontendMasters%20Full%20Stack%2FHow%20to%20ssh%20into%20your%20server), then ssh into the droplet server
3. update software then restart
4. create a new user
5. enable login for new user
6. disable root login

## detailed steps
### update software then restart
1. ssh into your server
2. `apt update` then `apt upgrade`
3. `shutdown now -r` this tells the server to shutdown immediately then restart
Just tab into `<ok>` then press enter if something pops up.

### create a new user
1. `adduser <your_username>`
2. `usermod -aG sudo <your_username>` add user to sudo group
3. `su <your_username>` switch user
4. `sudo cat /var/log/auth.log` check sudo access

### enable login for new user
1. create `authorized_keys` file
2. paste your public key (on your local machine, some file in `~/.ssh/` that ends in `.pub`)
3. exit server (type in `exit`)
4. login as new user `ssh albert@<do_droplet_ip>`

### disable root login
1. `chmod 644 ~/.ssh/authorized_keys`
2. `sudo vi /etc/ssh/sshd_config` disable root login
	1. scroll down to find `PermitRootLogin yes` change it to `no`
3. `sudo service sshd restart` restart ssh daemon
