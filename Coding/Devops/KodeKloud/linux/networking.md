### **1. `ip link` - List and Modify Network Interfaces**

- **What it does**: Shows all network interfaces (physical/virtual) and their status (UP/DOWN).
    
- **Examples**:
    - `ip link show` → Lists all interfaces (e.g., `eth0`, `wlan0`, `lo`).
    - `ip link set eth0 up` → Brings `eth0` up (enables it).
    - `ip link set eth0 down` → Disables `eth0`.

---

### **2. `ip addr` - Show IP Addresses Assigned to Interfaces**

- **What it does**: Displays IP addresses, MAC addresses, and interface states.
- **Examples**:
    - `ip addr show` → Lists all interfaces with their IPs (like `ifconfig`).
    - `ip addr show eth0` → Shows details only for `eth0`.

---

### **3. `ip addr add 192.168.1.10/24 dev eth0` - Assign an IP to an Interface**

- **What it does**: Temporarily assigns an IP address (`192.168.1.10`) to `eth0` with a subnet mask (`/24` = `255.255.255.0`).
- **Note**: This change is **not permanent** (will reset after reboot).
    
---

### **4. `/etc/netplan/*.yaml` - Permanent Network Configuration (Ubuntu)**

- **What it does**: Modern Linux (Ubuntu) uses Netplan YAML files to define network settings.
- **Example** (`/etc/netplan/01-netcfg.yaml`):
    network:
      version: 2
      ethernets:
        eth0:
          addresses: [192.168.1.10/24]
          gateway4: 192.168.1.1
          nameservers:
            addresses: [8.8.8.8, 8.8.4.4]
- **Apply changes**:
    `sudo netplan apply`

---

### **5. `ip route` - Show Routing Table**

- **What it does**: Displays how traffic is routed (which gateway is used for which network).
- **Example output**:
    default via 192.168.1.1 dev eth0  # Default route (Internet)
    192.168.1.0/24 dev eth0          # Local network

---

### **6. `ip route add 192.168.1.0/24 via 192.168.2.1` - Add a Static Route**

- **What it does**: Tells the system to send traffic for `192.168.1.0/24` via `192.168.2.1`.
- **Use case**: Needed when devices are behind another router (e.g., VPNs or subnets).
- **Note**: Like `ip addr add`, this is temporary. For permanence, add it to Netplan or `/etc/network/interfaces`.

---

### **Summary Table**

|Command/File|Purpose|
|---|---|
|`ip link`|Manage interfaces (up/down, rename, etc.)|
|`ip addr`|View/set IP addresses|
|`ip addr add`|Temporarily assign an IP|
|`/etc/netplan/*.yaml`|Permanent IP/gateway/DNS settings|
|`ip route`|View routing table|
|`ip route add`|Temporarily add a route|