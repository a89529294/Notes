1. `cd ~/.ssh` on your local machine
2. `ssh-keygen` then type in filename to store `file_name`(secret key) and `file_name.pub`(public key)
3. `ssh -i file_name root@server_ip` you can also omit the `-i file_name`, ssh will automatically try every private key file.
4. if it's the first time, choose continue to add the server to `known_hosts`
5. `exit` to exit server
6. after you go through [this](obsidian://open?vault=notes&file=Coding%2FCourses%2FFrontendMasters%20Full%20Stack%2FFlowchart%20of%20updating%20and%20restarting%20a%20brand%20new%20server) you should ssh into your droplet using `ssh albert@<ip_address>` 