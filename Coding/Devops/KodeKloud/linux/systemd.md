## __systemd vs pm2__

`systemd` and `PM2` are both process managers, but they serve different ecosystems and have distinct design goals. Here’s a breakdown of their similarities and differences:

### **Similarities**

1. **Process Management**    
    - Both can start, stop, restart, and monitor applications.
    - Both ensure that processes stay alive (auto-restart on crashes).
        
2. **Logging**
    - Both capture and manage logs (`systemd` via `journald`, PM2 via its built-in log system).
        
3. **Boot-time Startup**
    - Both can start applications at system boot (`systemd` natively, PM2 via `pm2 startup` which generates a `systemd`/`init` script).
        
4. **Monitoring**
    - Both provide process status visibility (`systemctl status` vs. `pm2 list`).
        
---
### **Differences**

|Feature|`systemd`|`PM2`|
|---|---|---|
|**Primary Use Case**|System-wide service management (Linux)|Node.js application management (but can manage other processes)|
|**Ecosystem**|Default on most Linux distros|Designed for Node.js (but supports Python, Ruby, etc.)|
|**Cluster Mode**|Not built-in (requires manual setup)|Built-in clustering for Node.js apps|
|**Load Balancing**|No|Yes (via PM2’s cluster mode)|
|**Hot Reload**|No (restart required)|Yes (`pm2 reload`)|
|**Configuration**|Uses `.service` files (INI-style)|Uses `ecosystem.config.js` (JavaScript)|
|**Log Management**|Via `journalctl`|Built-in log rotation & file output|
|**GUI**|No (CLI only)|Web-based dashboard (`pm2 monitor`)|
|**Dependencies**|Part of Linux|Requires Node.js runtime|

### **When to Use Which?**

- Use **`systemd`** for:
    - Managing system services (e.g., databases, web servers).
    - Low-level Linux process control.
    - Services requiring tight OS integration.
        
- Use **PM2** for:
    - Node.js applications (especially in production).
    - Zero-downtime reloads and clustering.
    - Developer-friendly process management.

## **Steps to Create a `systemd` Service:**

1. **Create a `.service` file** (e.g., `myapp.service`) in `/etc/systemd/system/`:
    
    [Unit]
    Description=My Custom Application
    After=network.target
    
    [Service]
    Type=simple
    User=myuser
    WorkingDirectory=/path/to/app
    ExecStart=/usr/bin/node /path/to/app/index.js
    Restart=always
    Environment="NODE_ENV=production"
    
    [Install]
    WantedBy=multi-user.target
    
2. **Reload `systemd`** to recognize the new service:
    sudo systemctl daemon-reload
    
3. **Start & Enable the Service**:    
    sudo systemctl start myapp
    sudo systemctl enable myapp  # Enable auto-start on boot
    
4. **Check Status**:
    sudo systemctl status myapp

## __multi-user.target__ vs __graphical.target__

- [Install] section is for when to start the service during reboot
	- **Always default to `multi-user.target` unless your service _explicitly requires a GUI_** (like a desktop app, Electron, or a browser-based tool).
## __restart=always__ vs __restart=on-failure__

**The _only_ behavioral difference** between `Restart=always` and `Restart=on-failure` is how they handle a **clean exit (status `0`)**. Here’s the distilled answer:

---
### **1. Identical Behavior For**

Both settings will:  
✅ Restart if:
- Process crashes (non-zero exit, e.g., `exit 1`).
- Process is killed (e.g., `kill -9`, `SIGSEGV`).
- You run `systemctl restart`.

❌ **Not restart** if:
- You run `systemctl stop`.
- Service is disabled (`systemctl disable`).

---
### **2. The _Only_ Difference**

|Exit Code|`Restart=always`|`Restart=on-failure`|
|---|---|---|
|**`0` (success)**|✅ Restarts|❌ **Stays stopped**|
|**`1+` (failure)**|✅ Restarts|✅ Restarts|

## __[Install] vs systemctl enable__

- The `[Install]` section **defines** how the service should be enabled.    
- `systemctl enable` **executes** the enabling based on that definition.

## __Commands__

- `systemctl start docker`
- `systemctl stop docker`
- `systemctl restart docker`
- `systemctl reload docker`
- `systemctl enable docker`
- `systemctl disable docker`
- `systemctl status docker`
- `systemctl daemon-reload` run this after modification to a `.service` file
- `systemctl edit docker.service --full`, edit `.service` file, this way you don't need to run `systemctl daemon-reload` afterwards
- `systemctl list-units --all`: **Loaded** units (active/inactive)
- `systemctl list-unit-files`: **All installed** unit files (even unused)
	- **`list-units --all`** → "What is systemd currently tracking?"
	- **`list-unit-files`** → "What unit files exist on disk?"
	- **`daemon-reload`** → Syncs disk changes into systemd’s memory.

## __journalctl__

- `journalctl` all log entries
- `journalctl -b` log entries from current boot
- `journalctl -u docker.service`