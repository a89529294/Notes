1. `curl https://deb.nodesource.com/setup_20.x | sudo -E bash -`
2. `sudo apt-get install nodejs -y`

Alternatively use _nvm_ to install node
1. `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash`
2. exit out of vps, then ssh back in
3. run `command -v nvm` if you see `mvn` printed back it worked.
4. `nvm install --lts`