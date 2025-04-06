### **Global → Regional → Zonal → Subnet Level**

| **Level**   | **Example**                   | **What It Means**                                                                     |
| ----------- | ----------------------------- | ------------------------------------------------------------------------------------- |
| **Region**  | `ap-northeast-2` (Seoul)      | A physical AWS location with multiple **Availability Zones (AZs)**.                   |
| **AZ**      | `ap-northeast-2a`, `2b`, etc. | Isolated data centers within a region (for redundancy).                               |
| **VPC**     | `vpc-08e03dc12106e2598`       | Your private network inside AWS (spans **all AZs in the region**).                    |
| **Subnet**  | `subnet-0b252f6cf4cbadc35`    | A segment of the VPC’s IP range, tied to **one AZ** (public or private).              |
| **EC2/RDS** | `i-1234567890abcdef0`         | Your actual compute/database resources, deployed in **one subnet (and thus one AZ)**. |

- _CIDR_ A CIDR block defines the ip addresses that resources in the VPC can use
- The __first 4 and the last IP address of a subnet CANNOT be used__. This means for _subnet-1_ `192.168.10.0/24` the following cannot be used
	- `192.168.10.0`,`192.168.10.1`,`192.168.10.2`,`192.168.10.3`
	- `192.168.10.255` (broadcast address)
- Access to _internet gateway_ determines whether a _subnet_ is public or private.
	- _NAT gateway_ can provide internet access to _subnets_ as well, but the connection must be initiated within the VPC.
	- The Flow When Using NAT Gateway:
		1. You create a NAT Gateway in a **public subnet** (it must be in a public subnet with an IGW route)
		2. You update the route table of your **private subnets** to direct internet-bound traffic (0.0.0.0/0) to the NAT Gateway instead of directly to IGW
		3. When an instance in a private subnet needs internet access:
		    - It sends traffic to the NAT Gateway
		    - The NAT Gateway (in the public subnet) forwards the traffic to the IGW
		    - Return traffic comes back through the same path