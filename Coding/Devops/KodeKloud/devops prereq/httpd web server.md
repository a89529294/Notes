1. Apache web server **is** `httpd`—they are the same thing, just different names.
2. `httpd` is available in CentOS's package repositories, so you can install it using `sudo yum install httpd` (or `sudo dnf install httpd`). It installs a precompiled binary package, not source code.
3. By default, **most** ports are blocked by the firewall, including HTTP (port 80) and HTTPS (port 443). You need to explicitly allow these ports or services.
```bash
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload
```
4. You can check what is allowed or blocked by the firewall using commands like:
    - `firewall-cmd --list-services`, prefer this one
    - `firewall-cmd --list-ports`
    - `firewall-cmd --list-all`

## httpd/apache web server
- `/var/log/httpd/access_log`, `/var/log/httpd/error_log`
- `/etc/httpd/conf/httpd.conf` config file
- don't use `service httpd start`, `service` is only available on older systems. 
```bash
# Start the service
sudo systemctl start httpd

# Stop the service
sudo systemctl stop httpd

# Restart the service
sudo systemctl restart httpd

# Enable service to start on boot
sudo systemctl enable httpd

# Check service status
sudo systemctl status httpd
```
