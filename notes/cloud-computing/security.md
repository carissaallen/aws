# Security in the Cloud

## [Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)
While AWS manages security _of the cloud_, security _in the cloud_ is the responsibility of the customer.

Customers retain control of what security they choose to implement to protect their own content, platform, applications, systems and networks, no differently than they would in an on-site data center.

**Example:**
If you forgot to update the security patches on your EC2 Instances and you get hacked--this is your responsibility. Responsible for IAM, customer data, operating systems on your EC2 instances, etc.

**Example:**
AWS is responsible for security of the hardware, availability regions, any software on those stacks (virtualization or application software, such as IDS or SQL Server).

[Shared Responsibility Model (Song)](https://www.youtube.com/watch?v=tIb5PGW_t1o)

<img src="https://github.com/carissaallen/aws/blob/master/notes/cloud-computing/Shared_Responsibility_Model.jpg">

## AWS WAF
WAF = Web applicaton firewall 

	- Helps protect your web applications from common web exploits that could affect application availability, compromise security, or consume excessive resources.
	- Layer 7 firewall (at the application layer), protects against hackers.
	- If a WAF is in front of your load balancer, it will not pass the attack (SQL injection, cross site scripting, etc.) through to your EC2 Instance.

## AWS Shield
A managed Distributed Denial of Service (DDoS) protection service that safeguards web applications running on AWS. 
	- Provides always-on detection and automatic inline mitigations that minimize application downtime and latency, so there is no need to engage AWS Support to benefit from DDoS Protection.
	- Designed to stop DDoS attacks.
		- Standard Tier
		- Advanced Tier 

## AWS Inspector (Security, Identity & Compliance)
_Inspects EC2 instances for vulnerabilities._

An automated security assessment service that helps improve the security and compliance of applications deployed on AWS.
	- Automatically assesses applications for vulnerabilities or deviations from best practices.
	- After performing an assessment, it produces a detailed list of security findings prioritized by level of severity.
	- These findings can be reviewed directly or as part of detailed assessment reports, available via the Inspector console or API.

It's an agent that you install on your EC2 Instances; it will review the EC2 instances for common vulnerabilities (e.g., need to update security patches). 

## Trusted Advisor (Management & Governance)
_Inspects your AWS account as a whole (not just EC2). It does Security, Cost Optimization, Performance, and Fault Tolerance._

An online resource to help you reduce cost, increase performance, and improve security by optimizing your AWS environment. 
	- Provides real time guidance to help you provision your resources following AWS best practices.
	- Will advise you on Cost Optimization, Performance, Security, Fault Tolerance.
	- (1) Core Checks and Recommendations
	- (2) Full Trusted Advisor (Business/Enterprise accounts only)

## Cloud Trail (Management & Governance)
Increases visibility into your user and resource activity by recording AWS Management Console actions and API calls. 
	- You can identify which users and accounts called AWS, the source IP address from which the calls were made, and when the calls occurred.
	
## Quiz Answers
- [Compliance Programs](https://aws.amazon.com/compliance/programs/)
- Trusted Advisor helps you optimize your entire AWS environment in real time following AWS best practices. It helps you optimize cost, fault-tolerance, and more.
- AWS Inspector assesses the security and compliance of your EC2 instances.
- A PCI DSS Level 1 certification attests to the security of the AWS platform regarding credit card transactions.
- WAF operates down to Layer 7.
- AWS Shield is AWS' managed DDoS protection service.
- AWS Trusted Advisor can help you assess the fault-tolerance of your AWS environment.
- It's safer to use IAM roles than it is to use Access Keys.
- Only AWS Shield Advanced offers automated application layer monitoring.
 
