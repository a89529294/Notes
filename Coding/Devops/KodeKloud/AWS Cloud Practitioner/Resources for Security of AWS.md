## Prevention
### AWS Web Application Firewall (WAF)
Amazon Web Application Firewall (AWS WAF) is designed to monitor and protect web applications against common threats like SQL injection, cross-site scripting (XSS), and bot attacks. Here’s how it works:

### What web apps are protected
AWS WAF can protect web applications deployed in multiple AWS services, including:
- **Amazon CloudFront** (CDN)
- **Application Load Balancer (ALB)**
- **Amazon API Gateway**
- **AWS App Runner**
- **AWS AppSync**

It **does not** automatically protect EC2 instances **unless** they are behind an **Application Load Balancer (ALB)** or a similar AWS-managed service that integrates with AWS WAF. If your EC2-hosted web app is directly exposed (e.g., running on an Nginx/Apache server), AWS WAF won’t protect it unless you configure a reverse proxy or use CloudFront in front of it.

### How does AWS WAF monitoring works
AWS WAF examines HTTP(S) requests as they pass through an integrated AWS service (e.g., CloudFront, ALB, API Gateway). It analyzes these requests using **WebACL rules** that you configure.

#### **How It Determines Suspicious Requests**

AWS WAF uses **rules and rule groups**, which can be:

- **Managed rules** from AWS (e.g., AWS Common Rules for OWASP Top 10 threats)
- **Custom rules** you define (e.g., block traffic from certain countries or IPs)
- **Rate-based rules** that detect unusual request patterns (e.g., too many requests from a single IP)

AWS WAF checks each request against these rules and assigns an **action** based on matching conditions.

#### **What Happens If a Request is Suspicious?**

If a request matches a rule, AWS WAF can:

1. **Allow the request** – If it’s considered safe.
2. **Block the request** – If it matches a rule you set.
3. **Count the request** – If you’re monitoring traffic without enforcing rules yet.
4. **Challenge the request** – Using AWS WAF CAPTCHA or JavaScript challenge for bot mitigation.

### AWS Shield
Detects and mitigates distributed denial of service (DDoS) attacks.

### AWS Network Firewall
Stateful firewall to protect traffic entering and leaving a virtual private cloud (VPC).

### Key Differences between WAF and Network Firewall

| Feature                | AWS WAF                                  | AWS Network Firewall                                      |
| ---------------------- | ---------------------------------------- | --------------------------------------------------------- |
| **Layer of Operation** | Application Layer (Layer 7)              | Network Layer (Layer 3/4) and Application Layer (Layer 7) |
| **Primary Purpose**    | Protects web applications and APIs       | Protects the entire VPC and network traffic               |
| **Traffic Type**       | HTTP/HTTPS traffic                       | All IP traffic (TCP, UDP, ICMP, etc.)                     |
| **Integration**        | CloudFront, ALB, API Gateway             | VPC, Transit Gateway, Direct Connect, VPN                 |
| **Customization**      | Web-specific rules (e.g., SQL injection) | Network-level rules (e.g., IP, port, protocol)            |
| **Use Case**           | Web application security                 | Network-wide security                                     |

## Detection

### AWS Inspector
- Scans workloads running on AWS for vulnerabilities. 
- Automatically discovers EC2 instances, container images in ECR and lambda functions.
- Automatically re-run scans whenever changes that could introduce vulnerabilities are made
	- installing new packages
	- installing patch

### AWS GuardDuty
- Can be enabled with a few clicks in AWS console
- Monitors suspicious activities
	- Abnormal API activity
	- Attempts to disable CloudFront logging
	- S3 bucket compromise
- Detect threats: with machine learning and anomaly detection to identify potential threats.

### Amazon Detective
- ingests data from VPC flow logs, CloudTrail logs and GuardDuty findings
- creates visualization that shows resource behaviors and interactions over time

### AWS Config
- tracks and audits the configuration of AWS resources over time.

### AWS Security Hub
- Automates security checks and brings security alerts into a central location
	- Amazon Inspector
	- Amazon GuardDuty
- A comprehensive security service that helps you centrally manage security and compliance across multiple AWS accounts. It aggregates and prioritizes security findings from various AWS services, third-party products, and custom integrations, providing a unified view of security posture across your AWS environment.
### CloudTrail
- tracks user activity within an account
- anytime a user performs an action, an event is logged
	- user logs in
	- modifying policies
	- access/create/delete/update a service

### Security Lake
is a centralized data lake service that aggregates, normalizes, and manages security-related log from various sources across your AWS environment and third-party services.
- on prem
- AWS
- third parties

### AWS Macie
- Uses pattern matching and deep learning to discover sensitive data, e.g. personal data, credit card number.
- generates a report of s3 buckets and scan objects for sensitive data

## Management

### Firewall Manager
central place to manage firewall and security policies
- AWS Shield
- AWS WAF
- AWS Network Firewall

### Resource Access manager (RAM)
Allows you to securely share AWS resources across multiple accounts within your organization or with external accounts, simplifying resource management and reducing the need for duplicate resources.

To share an Amazon VPC using Amazon RAM, first create a VPC in the source account (Account A). Then, in Account A, create a resource share in RAM, selecting the VPC and adding the destination account (Account B) as a principal. Finally, in Account B, accept the shared resource in RAM, allowing it to use the VPC in its own account.

### AWS Cognito
Customer identity and access management for web and mobile apps.

### Identity and Access Management (IAM)
Manages access to AWS resources.

### IAM Identity Center
Enables centralized management of user identities and access to AWS resources and applications. Unlike IAM, which provides fine-grained control over AWS resources for individual users or roles, IAM Identity Center simplifies identity and access management by allowing users to sign in once to access multiple AWS accounts and applications.

### Secrets Manager
- Applications will need access to credentials/secrets to perform tasks
	- You don't want to hardcode them into source code.
	- Credentials can be stored and managed in AWS Secrets Manager.

### AWS Certificate Manager (ACM)
Handles creating/storing and renewing public/private certificates
[[- Example on Using AWS Certificate Manager]]

### AWS Private Certificate Authority
AWS Private Certificate Authority (PCA) is a fully managed service that enables you to create and manage your own private SSL/TLS certificates for internal applications and resources within your organization.

### Key Management System (KMS)
AWS Key Management Service (KMS) is a managed service that allows you to create and control cryptographic keys for your applications. You can use KMS to *encrypt data at rest*, in transit, and for other cryptographic tasks.
[[- Example on KMS]]

### Cloud Hardware Security Module (HSM)
A cloud-based service that provides hardware-based key management and cryptographic operations to securely manage and protect sensitive data.
[[- Example on Cloud Hardware Security Module]]