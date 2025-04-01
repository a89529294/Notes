It is responsible for the reliable transfer of data between two nodes on the same network segment. This layer defines protocols for the access and use of the physical network, such as addressing, flow control, and error detection and correction.

## **Ethernet Frame Structure (IEEE 802.3)**

|Field|Size (Bytes)|Description|
|---|---|---|
|**Destination MAC**|6|MAC address of the receiving device.|
|**Source MAC**|6|MAC address of the sending device.|
|**EtherType (or Length)**|2|Indicates either:  <br>- The **L3 protocol type** (if ≥ `0x0600`, e.g., `0x0800` for IPv4, `0x86DD` for IPv6).  <br>- Or the **length** of the payload (if ≤ `0x05DC`).|
|**Payload (Data)**|46–1500|The actual data passed down from **Layer 3 (Network Layer)**.|
|**FCS (Frame Check Sequence)**|4|CRC checksum for error detection (optional in some modern networks).|

### **Clarifications:**

1. **"L3 Protocol" (EtherType)**:
    - The **EtherType** field tells the receiving device which **Layer 3 (Network Layer)** protocol is encapsulated in the payload.
    - Examples:
        - `0x0800` → **IPv4**
        - `0x86DD` → **IPv6**
        - `0x0806` → **ARP**
        - `0x8100` → **VLAN-tagged frame (IEEE 802.1Q)**
2. **Payload Size (46–1500 Bytes)**:
    - **Minimum (46 bytes)**: Ensures the frame meets the **64-byte minimum** (header + payload + FCS). If data is smaller, padding is added.
    - **Maximum (1500 bytes)**: Traditional **MTU (Maximum Transmission Unit)** for Ethernet. Jumbo frames (up to 9000 bytes) are also supported in some networks.
3. **"IP" as an L3 Protocol**:
    - **IP (Internet Protocol)** is the most common **Layer 3 protocol** (e.g., IPv4, IPv6).
    - Other L3 protocols (like **IPX, ICMP, or ARP**) can also be carried in Ethernet frames, but IP dominates modern networks.    

### **Key Takeaways:**
- The **Data Link Layer (L2)** adds **MAC addresses** and **EtherType** to identify where the frame goes and what’s inside.
- The **Network Layer (L3)** provides the **payload** (e.g., an IP packet).
- **EtherType** tells the receiver how to interpret the payload (e.g., as an IP packet, ARP message, etc.).

## **1. IP is Both an Address _and_ a Protocol**

- **IP (Internet Protocol)** is a **Layer 3 (Network Layer) protocol** that defines:
    - **Addressing** (e.g., `192.168.1.1` for IPv4, `2001:db8::1` for IPv6).
    - **Packet structure** (how data is formatted for transmission).
    - **Routing rules** (how packets move across networks).
- When we say **"IP packet"**, we mean a structured chunk of data that includes:
    - **Source & Destination IP addresses** (like envelopes in mail).
    - **Payload** (the actual data from higher layers, like a TCP segment).
    - **Control info** (e.g., version, TTL, checksum).