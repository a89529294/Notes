## connecting vps and github
1.  On the remote vps, `ssh-keygen -t ed25519 -C "description here"`
2. Copy the public key to github.
3. On remote vps, `touch ~/.ssh/config`, add
```txt
Host github.com
    IdentityFile ~/.ssh/<name of private key file>
```

## clone and build app
1. `mkdir ~/apps`
2. `cd ~/apps`
3. `git clone git@github.com:yourusername/yourrepo.git`
4. `cd yourrepo`
5. `pnpm install && pnpm run build`

## setup directory
1. `sudo mkdir -p /var/www/app`
2. `sudo cp -r dist/* /var/www/app`
3. `sudo chown -R $USER:www-data /var/www/app`
	1. make sure the default web server user is `www-data` by running `cat /etc/nginx/nginx.conf | grep user` 
4. `sudo chmod -R 755 /var/www/app`