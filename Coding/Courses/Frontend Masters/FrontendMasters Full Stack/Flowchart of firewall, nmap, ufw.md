1. install map using brew `brew install nmap`
2. on local machine run `nmap <ip-of-remote-server>`
3. ssh into remote server
4. `sudo ufw status` check if _ufw_ is on, _ufw_ is the uncomplicated _firewall_
5. `sudo ufw allow ssh`
6. `sudo ufw allow http`
7. `sudo ufw enable`
8. __IF__ you want to disable a port run `sudo ufw deny http` for example.
9. back on local machine `nmap <ip-of-remote-server>` to make sure only the ports we allowed are open