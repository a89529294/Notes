### **AWS Network-Level Firewalls (Broadest Scope)**

- **AWS Shield** – Protects against DDoS attacks at the network (Layer 3/4) and application (Layer 7) levels (Advanced tier for enhanced protection).
- **AWS Network Firewall** – A managed stateful firewall for VPCs, offering deep packet inspection, intrusion prevention (IPS), and custom rule sets.
- **AWS WAF (Web Application Firewall)** – Protects web applications (HTTP/HTTPS) from common exploits like SQLi, XSS, and OWASP Top 10 threats.
- **AWS Route 53 Resolver DNS Firewall** – Filters DNS queries to block malicious domains.

### **2. VPC & Subnet-Level Firewalls**

- **NACLs (Network Access Control Lists)** – Stateless firewall rules at the subnet level (allow/deny traffic based on IP/port).
- **Security Groups (SGs)** – Stateful virtual firewalls for EC2 instances, RDS, Lambda, etc., enforcing rules at the instance level.

### **3. Instance/OS-Level Firewalls**

- **EC2 Instance OS Firewall (e.g., iptables/nftables for Linux, Windows Firewall for Windows)** – Controls traffic at the OS level.
- **UFW (Uncomplicated Firewall, Linux)** – A simplified frontend for iptables.
- **Firewalld (Linux, RHEL/CentOS)** – Dynamic firewall manager with zones.

### **4. Container & Application-Level Firewalls (Narrowest Scope)**

- **AWS App Mesh & Service Mesh (e.g., Istio, Envoy Proxy)** – Microservices-level traffic control (mTLS, rate limiting).
- **Container Network Security (e.g., Docker/ECS/EKS network policies, Calico, Cilium)** – Controls pod-to-pod traffic in Kubernetes.
- **Application-Specific Firewalls (e.g., ModSecurity for Apache/Nginx, Cloudflare WAF for apps)** – Embedded web app protection.

### **Even Narrower?**

- **Library/Code-Level Security (e.g., OPA/Gatekeeper, embedded TLS enforcement)** – Fine-grained policy enforcement within apps.