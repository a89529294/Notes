## __ssh__
- ensure you have a ssh daemon running on the remote server
- `ssh keygen -t ed25519` on client
	- the generated key pair would be in `~/.ssh`
	- `~/.ssh/id_ed25519` is the private key
	- `~/.SSH/id_ed25519.pub` is the public key
- `ssh-copy-id -i ~/.ssh/ed_25519.pub user@host`
	1. Reads your local public key
	2. Connects to the remote server via SSH (you'll need to enter your password)
	3. Appends your public key to `~/.ssh/authorized_keys` on the remote server
	4. Sets appropriate permissions (creates `~/.ssh` with 700 permissions and `authorized_keys` with 600 if they don't exist)
- login using private key `ssh -i ~/.ssh/ed_25519 user@host`
- disable root login
```bash
# Set proper permissions:
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

# Disable root login (good practice):
sudo sed -i 's/^PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config

# Optionally disable passwords (after verifying key auth works):
sudo sed -i 's/^PasswordAuthentication.*/PasswordAuthentication no/' /etc/ssh/sshd_config

# Restart SSH:
sudo systemctl restart sshd  # or sudo service ssh restart	
```

## __scp__
ssh + cp

- `scp code.tar.gz user@host:path-to-dir`
- `scp -pr dir user@host:path-to-dir` -p: preserve ownership, -r: recursive