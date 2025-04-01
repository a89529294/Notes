## Key Networking Concepts in Linux

### 1. Network Interfaces

These are the points where your computer connects to a network. They can be:

- **Physical interfaces**: Like `eth0` (Ethernet) or `wlan0` (WiFi)
- **Virtual interfaces**: Like `lo` (loopback) or `tun0` (VPN tunnel)
    
You can see them with: `ip link show`

### 2. IP Addresses

Each interface can have one or more IP addresses (v4 or v6):

`ip addr show`

### 3. Network Configuration Files

On different distributions, these are stored in different locations:

- **Debian/Ubuntu**: `/etc/network/interfaces`
- **RHEL/CentOS**: `/etc/sysconfig/network-scripts/ifcfg-<interface>`
- **Systemd systems**: `.network` files in `/etc/systemd/network/`

### 4. Network Manager

Many modern distros use NetworkManager which adds a management layer:
```bash
nmcli device status  # List devices
nmcli connection show  # Show connections
```

### 5. Routing

How your system decides where to send network traffic:
`ip route show`

### 6. DNS Resolution

Configured in:
- `/etc/resolv.conf` (but often managed dynamically)
- `/etc/hosts` for local name resolution
- `/etc/nsswitch.conf` controls resolution order

## Common Commands

|Purpose|Command|
|---|---|
|View interfaces|`ip link`, `ip addr`|
|Configure interface|`ip addr add 192.168.1.10/24 dev eth0`|
|Bring interface up/down|`ip link set eth0 up/down`|
|Check connectivity|`ping google.com`|
|Show routing|`ip route`|
|Show open ports|`ss -tulnp` (or `netstat -tulnp`)|
|Trace network path|`traceroute google.com`|
|DNS lookup|`dig google.com` or `nslookup google.com`|

## Example Workflow

1. Check what interfaces exist:
	`ip link show`
    
2. Check IP addresses:
    `ip addr show`
    
3. Check network connectivity:
    `ping -c 4 8.8.8.8`
    
4. Check if DNS works:
    `ping -c 4 google.com`
    
5. See your route to the internet:
    `ip route show`

## Common Confusions

1. **Interface vs Connection**:
    
    - An interface is the hardware/software network port
    - A connection is a configuration applied to that interface
        
2. **Static vs Dynamic IP**:
    
    - Static: Manually configured and permanent
    - Dynamic: Assigned by DHCP server (common in home networks)
        
3. **NetworkManager vs systemd-networkd**:
    
    - Different tools that can manage networking
    - Some distros use one, some the other, some both