### **Step 1: Launch the EC2 Bastion Host**

1. **AMI**: Use **Amazon Linux 2023** or **Ubuntu 22.04 LTS** (default AMIs have SSM Agent preinstalled).
2. **Instance Type**: `t3.micro` (free tier eligible).
3. **Key Pair**: Attach your existing key pair (e.g., `my-key.pem`).  
    _(No password login needed—key auth is enforced by default.)_
4. **Network Settings**:
    - **VPC**: Same as your RDS instance.
    - **Subnet**: Public subnet (auto-assign public IP **enabled**).
5. **Security Group (SG)**:
    - **Rule 1**: Allow SSH from `0.0.0.0/0` (since only key holders can connect).
    - `Type: SSH | Port: 22 | Protocol: TCP | Source: 0.0.0.0/0`
### **Step 2: Configure the RDS Security Group**

6. Go to your RDS instance → **Security Groups** → Inbound rules.
7. Add a rule to allow the bastion host: `Type: PostgreSQL | Port: 5432 | Source: [EC2 Bastion’s Security Group]`
### **Step 3: Connect via SSH Tunnel (Local Machine)**

Run this command (replace placeholders):
`ssh -i ~/.ssh/my-key.pem -N -L 5433:your-rds-endpoint.rds.amazonaws.com:5432 ec2-user@ec2-bastion-public-ip`

### **Step 4: Connect to RDS via Localhost**

Use any PostgreSQL client (e.g., `psql`, DBeaver, TablePlus):
`psql -h localhost -p 5433 -U postgres -d your_db_name`
- **Username/Password**: Retrieve from AWS Secrets Manager (as before).

### **Troubleshooting**

- **"Connection refused"**: Verify RDS SG allows the bastion’s SG.
- **"Permission denied (publickey)"**: Ensure your local key has `400` permissions: `chmod 400 ~/.ssh/my-key.pem`