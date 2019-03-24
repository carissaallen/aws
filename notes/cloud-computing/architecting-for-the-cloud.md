# Architecting for the Cloud: Best Practices
**_Read the whitepaper._**

### Traditional Computing vs. Cloud Computing
* IT Assets are available as provisioned resources
  * CloudFormation allows us to have templates (using JSON) to create EC2 Instances, S3 Buckets, almost anything inside the AWS ecosystem.
    * Global, Available, and Scalable Capacity.
    * Higher Level Managed Services (for Machine Learning).
    * Built-in Security (IAM, etc.)
    * Architecting for Cost (can architect your environment to be cost-efficient).
    * Operations on AWS.
* Traditional Copmuting
  * Get a purchase order, purchase physical servers, 3-5 year contract, the servers would need to be racked, connected to the networking gear, must install the operating systems, etc.  

## Design Principles

### Scalability
**Scale Up**
* Increasing RAM or amount of CPU inside a virtual machine.
**Scale Out**
* Add multiple virtual machines behind an application load balancer, for example.
  * Stateless Applications (Lambda)
  * Distribute Load to Multiple Nodes (e.g., multiple EC2 servers, and database replicas)
  * Stateless Components 
    * Do not need to remember the information
  * Stateful Components 
    * Do not want to lose information; store in database or something stateful
    * Implement Session Affinity
      * **Sticky session**: put a cookie in a user's browser so every time they visit that website the Application Load Balancer will detect that cookie and send them back to that same EC2 Instance. You're "stuck" to a particular EC2 Instance.
    * Distributed Processing
    * Implement Distributed Processing
      * Elastic map reduce; it allows you to have a whole bunch of different EC2 Instances, and they process large, complex data. You have thousands of instances to reduce the time to process that data.
    * Instantiating Compute Resources
      * Bootstrapping (you do not want to manually configure your EC2 Instances; we can use a bootstrap script to install updates, or Word Press, for example)
      * Golden Images (set up autoscaling; took an image of our configured EC2 Instance for resuse)
      * Containers
      * Hybrid (containers and EC2 Instances)

### Infrastructure As Code
_Disposable Resources Instead of Fixed Servers._	
- CloudFormation

### Automation
- Serverless Mangement and Deployment
	- Using code pipeline, code deploy, etc.
- Infrastructure Mangement and Deployment
	- AWS Elastic Beanstalk
	- Amazon EC2 auto recovery
	- AWS Systems Manager
	- Auto Scaling

- Alarms and Events
	- Amazon CloudWatch alarms	
	- Amazon CloudWatch events
		- A way of having your environment proactively respond to a change in the environment.
	- AWS Lambda scheduled events
	- AWS WAF security automations
		- WAF: Web Application Firewall
		- Can automatically respond to someone doing something to your site (e.g., SQL Injection)

### Loose Coupling
- Well Defined Interfaces
	- Amazon API Gateway
		- Allows you to create your own APIs and expose them to the internet
- Service Discovery
	- Implement Service Discovery
		- If you have an EC2 Instance that needs to connect to an RDS instance using its DNS name with multiple AZ turned on, if the RDS instance fails, AWS will switch it to the other availability zone. Allows one component of AWS automatically discover another component of AWS.
- Asynchronous Integration
- Distributed Systems Best Practices
	- Graceful Failure in Practice
		- Example: If you have an S3 website and a page doesn't exist, you have an error.hmtl page to tell the users there has been a failure. Additionally, you have a mechanism to report this back to your system administrators. 

### Services Not Servers
_Use serverless services as much as possible so that servers do not have to be managed._

"No server is easier to manage than no server." - Werner Vogels (CTO, Amazon)

## Databases
Relational Databases (Aurora)
* Scalability 
* Will always have 6 copies of your data across 3+ availability zones
* Anti-patterns: would not use Aurora if you do not have a need for joins or complex transactions; use No-SQL instead

Non-Relational Databases (DynamoDB)
* Scalability
* High availability, multiple AZ
* Anti-patterns: requires joins or complex transactions, or you have large binary files

Data Warehouse (Redshift)
* Scalability
* High availability, multiple AZ  
* Anti-patterns: not meant for Online Transaction Processing (OLTP)

Graph Databases (Amazon Neptune)
* Scalability
* High Availability

### Managing Increasing Volumes of Data: Data Lake
An architectural approach that allows you to store massive amounts of data in a central location (like S3!) so it is readily available to be categorized, processed, analyzed, and consumed by diverse groups within your organization. 

Since data can be stored as-is, you do not have to convert it to a predefined schema, and you no longer need to know what questions to ask about your data beforehand.

Removing Single Points of Failure
* Introducing Redundancy
* Detect Failure
* Durable Data Storage
* Fault Isolation and Traditional Horizontal Scaling
* Sharding

Optimize for Cost
* Right Sizing
* Elasticity 
  * Your application will expand or contract depending on usage
* Take advantage of the variety of purchasing options (spot, reserverd, etc.)

Caching
* Application Caching
  * Using ElastiCache
* Edge Caching
* CloudFront

Security
* Use AWS Features for Defense in Depth
* Share Security Responsibility with AWS	
  * You and AWS are each responsibile for certain things
* Reduce Privileged Access (give developers _enough_ access to do their job)
* Security as Code 
* Real-Time Auditing
  * AWS Inspector and other security services
