## __Stateful__

- **Remembers requests and matches responses** to ensure they belong to an established, legitimate session.
- Example: If an internal host sends an HTTP request (outbound), the firewall allows the corresponding inbound HTTP response but blocks unsolicited inbound traffic.
## __Stateless__

- **No connection tracking**: A stateless firewall evaluates each packet **independently**, without remembering previous packets or sessions.
- **Rules must be explicitly defined for both directions**:
    - If you allow **inbound traffic on port 80 (HTTP)**, the firewall **does not automatically allow the corresponding outbound response**. 
    - **You must also explicitly allow outbound traffic** (e.g., high-numbered ephemeral ports for HTTP responses).
```txt
Allow Inbound: TCP 80 (HTTP request)  
Allow Outbound: TCP 1024-65535 (HTTP response)
```
## __NACL Network Access Control List__

- filter traffic entering and leaving a subnet
- _stateless_ firewalls, rules must be set for both _inbound_ and _outbound_ traffic

## __SG Security Group__

- acts as firewall for individual resource, e.g. _ec2_, _rds_. 
- _stateful_ firewall, so only the request needs to be allowed

## **Key Differences Between UFW and Security Groups:**

| Feature           | **Security Groups**                                             | **UFW (Uncomplicated Firewall)**                                   |
| ----------------- | --------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Scope**         | AWS network-level (applies before traffic reaches the instance) | OS-level (applies on the EC2 instance itself)                      |
| **Configuration** | Managed via AWS Console, CLI, or SDK                            | Managed via Linux commands (`ufw allow/deny`)                      |
| **Stateful**      | Yes (return traffic is automatically allowed)                   | Yes (can be configured to allow return traffic)                    |
| **Default Deny**  | All inbound traffic is denied by default                        | Depends on UFW configuration (`ufw enable` enforces default deny)  |
| **Persistence**   | Automatically persists across reboots                           | Requires enabling (`ufw enable`) to persist after reboot           |
| **Use Case**      | Controls access to/from EC2 instances at the AWS network level  | Controls traffic at the OS level (useful for additional filtering) |