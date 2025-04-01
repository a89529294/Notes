### **1. MAC Addresses (Layer 2 - Data Link)**

- **Purpose**: Deliver data **within the same local network** (e.g., between your computer and the router).
- **Format**:
    - 48-bit (e.g., `00:1A:2B:3C:4D:5E`).
    - Assigned by the manufacturer (burned into the NIC).
- **Analogy**:
    - Like the **recipient’s and sender’s names on an office mailroom envelope**.
    - Only relevant for delivery **inside the same building (local network)**.

#### **Where You See MAC Addresses**:

- Ethernet frames (Layer 2).
- Wi-Fi communications.
- Switches use MAC addresses to forward frames.

---

### **2. IP Addresses (Layer 3 - Network)**

- **Purpose**: Route data **across different networks** (e.g., from your home to a server on the internet).
- **Format**:
    - IPv4 (32-bit, e.g., `192.168.1.1`).
    - IPv6 (128-bit, e.g., `2001:0db8:85a3::8a2e:0370:7334`).
- **Analogy**:
    - Like the **postal address on a package** (city, state, ZIP code).
    - Used for **global routing** across the internet.

#### **Where You See IP Addresses**:

- IP packets (Layer 3).
- Used by routers to send data between networks.

---

### **3. How They Work Together (Step-by-Step)**

Let’s say you visit `google.com` from your laptop:

#### **Step 1: Your Laptop Prepares the Data**

- **Layer 4 (Transport)**: Encapsulates data in a **TCP segment** (with port numbers).
- **Layer 3 (Network)**: Wraps it in an **IP packet** with:
    - **Source IP**: Your private IP (e.g., `192.168.1.100`).
    - **Destination IP**: Google’s IP (e.g., `142.250.190.46`).
    
#### **Step 2: Your Laptop Builds the Ethernet Frame**

- **Layer 2 (Data Link)**: Adds MAC addresses for local delivery:
    - **Source MAC**: Your laptop’s MAC (e.g., `00:1A:2B:3C:4D:5E`).
    - **Destination MAC**: Your **router’s MAC** (not Google’s!).

Wait—**how does your laptop know the router’s MAC?**  
→ It uses **ARP** (Address Resolution Protocol) to find it!

#### **Step 3: The Frame Travels**

1. Your laptop sends the frame to the **router** (using MAC addresses).    
2. The router strips off the Ethernet header, checks the **IP packet**, and forwards it to the next hop (using IP routing).
3. Eventually, Google’s server replies, and the process reverses.

---

### **4. Key Differences**

|Feature|MAC Address (Layer 2)|IP Address (Layer 3)|
|---|---|---|
|**Scope**|Local network (LAN)|Global (internet-wide)|
|**Assigned by**|Manufacturer (NIC)|Network admin or DHCP|
|**Example**|`00:1A:2B:3C:4D:5E`|`192.168.1.1` or `142.250.190.46`|
|**Used by**|Switches, Wi-Fi APs|Routers|
|**Changes?**|Hardcoded (usually)|Dynamic (can change)|

---
### **5. Analogy Recap**

- **MAC Addresses** = Names on an **office mail envelope** (for internal delivery).
- **IP Addresses** = Postal addresses (for **global mail routing**).
- **Router** = The mailroom that takes internal envelopes and repackages them for external delivery.

---

### **Why Both Are Needed**

- **MAC addresses** ensure delivery **on the same network**.
- **IP addresses** ensure delivery **across networks**.
- Without MACs, switches wouldn’t know where to send frames.
- Without IPs, routers wouldn’t know how to reach the internet.

### **1. MAC Addresses: Change at Every Hop (Like Local Postmen)**

- **Why?** Because Ethernet/Wi-Fi links are **point-to-point** at Layer 2. Each device only cares about the "next hop’s" MAC.
- **Example**:
    - Your PC → Router:
        - **Source MAC**: Your PC’s MAC
        - **Dest MAC**: Router’s MAC
    - Router → ISP:
        - **Source MAC**: Router’s WAN MAC
        - **Dest MAC**: ISP’s MAC
    - ISP → Google:
        - **Source MAC**: ISP’s backbone router MAC
        - **Dest MAC**: Google’s edge router MAC
- **Key Point**: MACs are **rewritten by every router/switch** along the path.
    

---

### **2. IP Addresses: Mostly Stable, But With Exceptions**

#### **a) Private vs. Public IPs**
- **Private IP** (e.g., `192.168.1.100`):
    - Used **only inside your local network** (LAN).
    - **Stays the same** from your PC to your router.
- **Public IP** (e.g., `203.0.113.5`):
    - Assigned to your **router by your ISP**.
    - Seen by the **entire internet** as your network’s "return address."

#### **b) When IPs _Do_ Change**

1. **NAT (Network Address Translation)**:
    - Your router **replaces your private IP** with its public IP for outgoing traffic.
    - **Example**:
        - **Your PC sends**: Source IP = `192.168.1.100`, Dest IP = `142.250.190.46` (Google).
        - **Router rewrites**: Source IP = `203.0.113.5` (public IP), Dest IP unchanged.
        - **Google replies** to `203.0.113.5`, and your router translates it back to `192.168.1.100`.
2. **Carrier-Grade NAT (CGNAT)**:
    - Some ISPs share a **single public IP** among many customers (like an apartment building sharing one mailbox).
    - Adds _another layer_ of IP rewriting.
3. **Mobile Networks/VPNs**:
    - Your public IP changes when you switch networks (e.g., Wi-Fi → cellular).

#### **c) When IPs _Don’t_ Change**

- **End-to-End in the Public Internet**:
    - Google’s IP (`142.250.190.46`) **never changes**—it’s anchored to their servers.
    - Your public IP may change, but **not mid-connection** (usually).

---

### **3. Key Differences: MACs vs. IPs**

|Feature|MAC Addresses|IP Addresses|
|---|---|---|
|**Scope**|Local (per-hop)|Global (end-to-end, with NAT)|
|**Changes?**|**Every hop** (router/switch)|**Only at NAT boundaries**|
|**Example**|Your PC → Router → ISP → Google|Your PC (private) → Router (public) → Google|
|**Assigned by**|Manufacturer (NIC)|Network admin/ISP/DHCP|