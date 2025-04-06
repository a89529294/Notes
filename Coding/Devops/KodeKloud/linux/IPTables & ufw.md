`iptables` is a **firewall**, meaning it controls **whether traffic is allowed or blocked** on a Linux machine.

- On Ubuntu, you might need to install: `sudo apt install iptables`
- List rules: `sudo iptables -L`
- Rules are matched top to bottom - if one rule matches, the rest are discarded
- `ufw` is a frontend for `iptables`
  - Check status: `sudo ufw status verbose`
    ```
    Status: active  
    Logging: on (low)  
    Default: deny (incoming), allow (outgoing), deny (routed)
    ```
  - Allow incoming HTTP: `sudo ufw allow http`
  - Allow outgoing HTTP: `sudo ufw allow out http`
  - Deny incoming HTTP: `sudo ufw deny http`
  - Deny outgoing HTTP: `sudo ufw deny out http`
```bash
# 1. Allow SSH first (critical for remote servers!)
sudo ufw allow ssh

# 2. Enable UFW
sudo ufw enable

# 3. Add more rules (e.g., HTTP/HTTPS)
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

sudo ufw disable
sudo ufw reload # restarts ufw, rarely needed
sudo ufw reset # wipes all rules and resets to defaults
```