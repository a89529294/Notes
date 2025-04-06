#### **1. Subnets**

- **Definition:** A subnet is a segment of a VPC’s IP range, deployed in a single AZ.
- **Key Rules:**
    - Must be associated with **one route table** (default: main route table).
    - Can optionally have a **custom NACL** (default: VPC’s default NACL).
    - Instances in a subnet inherit its networking rules (NACL + route table).
    - **Public subnets** use a route table with an **Internet Gateway (IGW)**.
    - **Private subnets** use routes to **NAT Gateway/VPN**.
---
#### **2. Network ACLs (NACLs)**

- **Definition:** A stateless, optional firewall for subnets (operates at the subnet level).
- **Key Rules:**
    - **Rule Processing:** Evaluated **lowest to highest rule number** (e.g., Rule 100 → Rule 200 → `*`).
    - **Default NACL:** Allows all traffic (Rule 100: ALLOW ALL + `*` DENY ALL as a backup).
    - **Custom NACLs:** Explicitly define ALLOW/DENY rules (e.g., block SSH from the internet).
    - **Stateless:** Return traffic must be explicitly allowed (unlike Security Groups).
    - **Final Rule:** `*` (infinity) is an **implicit DENY** for unmatched traffic.
---
#### **3. Key Differences**

|Feature|Subnets|NACLs|
|---|---|---|
|**Scope**|AZ-specific IP range|Subnet firewall (optional)|
|**Association**|One route table, one NACL|One NACL per subnet (default or custom)|
|**Rule Priority**|N/A|Lowest rule number first|
|**Default Behavior**|Private unless routed via IGW|Allow All (default NACL)|

---
### **TL;DR**

- **Subnets** define **where resources live** (AZ + routing).    
- **NACLs** define **what traffic is allowed in/out of subnets** (stateless firewall).
- **Route tables** define **where traffic goes** (e.g., internet, VPN, local VPC).