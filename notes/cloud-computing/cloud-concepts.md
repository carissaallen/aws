## Cloud Computing
Cloud computing: on-demand delivery of compute, database storage, applications, and other IT resources through a cloud services platform via the internet with pay-as-you-go pricing. (Think of it as renting someone else's computer!)

Six advantages of cloud computing:
1. Trade capital expense for variable expense
	- not invested in data centers and servers before you know how you're going to use them 
	- paying only for actual consumption of resources
2. Benefit from massive economies of scale
	- Amazon has a larger purchasing power (they build their own servers!)
3. Not guessing about capacity
	- cloud can scale with business needs without a long-term contract
4. Increase speed and agility
	- it scales inifinitely with demand
	- no longer have to buy servers and rent data center space
5. Not spending money running and maintaining data centers
6. Go global in minutes
	- lower latency and better experience for customers

### Types of Cloud Computing: 
1. Infrastructure As A Service (IAAS): you manage a physical or virtual server; the data center provider will have no access to your server.
2. Platform As A Service (PAAS): someone else manages the underlying hardware and operating systems; you do not have to worry about security patching, updates, maintenance, etc. (ex: Elastic Beanstalk)
3. Software As A Service (SAAS): you only worry about the software, while someone else takes care of the data centers, servers, networks, storage, maintenance, patching, etc. (ex: Gmail)

### 3 Types of Cloud Computing Deloyments:
- Public Cloud (AWS, Azure, GCP)
- Hybrid (mixture of public and private)
- Private Cloud (On Premise); you manage it in your datacenter (Openstack, VMware)

### Core Services: 
- Compute 
	- EC2
	- Lambda
- Storage
	- S3: Simple Storage Service
	- Glacier	
- Databases
	- Relational Database Service (RDS)
	- DynamoDB (Non-relational Databases)
- Security, Identity, & Compliance
- AWS Cost Management
- Network
	- Route53
	- VPC

### AWS Global Infrastructure
- Availability Zone (AZ): one or more discrete data centers, each with redundant power, networking and connectivity, housed in separate facilities.
- Region: a geographical area in the world which consists of two or more Availability Zones.
- Edge location: endpoints for AWS used for caching content (typically this consists of CloudFront, Amazon's Content Delivery Network (CDN))

### Support Plans
- Basic
	- Access to community forums
- Developer
	- Technical support
	- Response time: 12-24 hours
	- Starts at $29/month
- Business
	- AWS Trusted Advisor
	- Response time: 1 hour
	- Starts at $100/month
- Enterprise
	- Technical Account Manager (TAM)
	- Response time: 15 minute
	- Starts at $15,000/month

## Identity Access Management (IAM)
- Global (you do not specify a region)
- Create a user or group (created globally)

### Access AWS platform in 3 ways:
- via the Console (console.aws.amazon.com)
- programmatically (using the command line)
- using the Software Developers Kit (SDK)

Root account: the email address you used to set up your AWS account.
	- has full administrator access
	- create a user for each individual within your organization
	- secure the root account using multi-factor authentication

Group: a place to store your users
	- users inherit all permissions that group uses
	- to set the permissions in a group, you must apply a policy to the group

Policy: consist of JSON (key value pairs)

## S3
S3: Simple Storage Service
	- A place to put your flat files (flat file: a file that doesn't change).
	- Object-based storage; allows you to upload files
	- Files 0 Bytes to 5 TB
	- There is unlimited storage
	- Files are sotred in Buckets (bucket must be a unique name globally)
	- S3 is a universal namespace (that is, names must be unique globally)
	- ex: https://s3-eu-west-1.amazonaws.com/acloudguru
	- Receive a HTTP 200 response code if upload was successful

S3 Object: think of Objects just as files.
	- Objects consist of:
		- Key: the name of the object
		- Value: the data, made up of a sequence of bytes
		- Version ID 
		- Metadata (data about the data you are storing)
		- Subresources
			- Access Control Lists
			- Torrent	
### Data Consistency for S3
1. Read after Write consistency 
	- PUTs of new Objects:
		- If you write a new file (putting a new file in S3) and read it immediately afterwards, you will be able to view the data immediately.
	- Overwrite PUTs (update an existing file, or delete a file)
		- When you read the file, you may get the older version
		- Changes to objects can take some time to propagate

### Features
- Tiered Storage Available
- Lifecycle Management
- Versioning
- Encryption
- Secure your data using Access Control Lists and Bucket Policies

### Storage Classes
- S3 Standard
	- stored redundantly across multiple devices in multiple facilities (designed to sustain the loss of 2 facilities concurrently)
- S3 IA (Infrequently Accessed)
	- data requires rapid access, for infrequent use; lower fee than S3, but you are charged a retrieval fee
- S3 One Zone IA
	- lower-cost option for infrequently accessed data, but do not require the multiple AZ data resilience
- S3 Intelligent Tiering
	- designed to optimize costs by automatically moving data to the most cost-effective access tier, without performance impact or operational overhead
- S3 Glacier
	- secure, durable, and low-cost storage class for data archiving; retrieval times configurable from minutes to hours
- S3 Glacier Deep Archive
	- lowest-cost storage class, where a retrieval time of 12 hours is acceptable

### Pricing
- Storage
- Requests
- Storage Management Pricing
- Data Transfer Pricing
- Transfer Acceleration
	- enables transfers of files over long distances between end users and an S3 bucket; takes advantage of CloudFront 
- Cross Region Replication Pricing
	- replicates file to a secondary bucket so you have disaster recovery

### Created an S3 bucket: Tips
- Bucket names share a common name space; you cannot have the same bucket name as someone else
- When you view your buckets, you vie them globally but you can have buckets in individual regions
- You can replicate the contents of one bucket to another bucket automatically using Cross Region Replication
- You can change the storage class and encryption on the fly 
	- S3 Standard
	- S3 IA
	- S3 One Zone IA
	- S3 Intelligent Tiering	
	- S3 Glacier
	- S3 Glacier Deep Archive
- Transfer Acceleration
	- Upload file to an Edge location, then Amazon uses those backbone networks to upload the file to its location

### Create an S3 Website
- You can use bucket policies to make entire S3 buckets public
- You can use S3 to host static websites (such as .html; no database connections)
- S3 scales to meet your demand; useful for a large number of requests

## CloudFront
- A content delivery network (CDN) is a system of distributed servers (network) that deliver webpages and other web content to a user based on teh geographic locations of the user, the origin of the webpage, and a content delivery server.

### Terminology
- Edge Location: the location where content will be cached (more of these than there are regions). This is separate to an AWS Region/AZ. You can read and write to Edge Locations.
- Origin: the origin of all the files that the CDN will distribute. This can be an S3 Bucket, an EC2 instance, an Elastic Load Balancer, or Route53.
- Distribution: this is the name given the CDN which consists of a collection of Edge Locations.
	- Web Distribution (typically used for websites)
	- RTMP (used for media streaming)
- TTL: Objects are cached for the life of TTL (Time To Live) in seconds.

Example: we have our origin in London (this is our S3 bucket containing our files). The users query the file (do you [Edge Location] have a copy of this file?). The Edge Location will not have the file upon this first query, and there will be added latency for this user. The Edge Location will connect to the origin and download the file, then stream it to the user. When the second user queries the same file; that file is already cached at the Edge Location, so the second user doesn't have to download it from the origin. They can get it from an Edge Location nearest them.

You can clear your cached objects, but you will be charged for doing that.

## EC2: Elastic Compute Cloud
A virtual server (or servers) in the cloud.
	- Reduces the time to obtain and boot new server instances to minutes,
	  allowing you to quickly scale capacity (up and down) as your computing requirements change

### Pricing Models
**On Demand**
	- Allows you to pay a fixed rate by the hour (or by the second) with no commitment
**Reserved**
	- Provides a capacity reservation, and offer a significant discount on thehourly charge for an instance
	- Contract terms are 1 year or 3 year terms
**Spot**
	- Enables you to bid whatever price you want for instance capacity
	- Provides for even greater savings if your applicans have flexible start/end times
**Dedicated Hosts**
	- Physical EC2 server dedicated for your use
	- Helps reduce costs by allowing you to use your existing server-bound software licenses

### EC2 Instance Types
Fight Dr. McPxz 
F - FPGA
I - IOPS
G - Graphics
H - High Disk Throughput
T - Cheap general purpose (think T2 Micro)
D - Density
R - RAM
M - Main choice for general pupose apps
C - Compute
P - Graphics (think Pictures)
X - Extreme Memory
Z - Extreme Memory and CPU

### EBS
_A virtual disk in the cloud that the virtual servers run off._

Allows you to create storage volumes and attach them to EC3 instances. Once attached, you can create a file system on top of these volumes, run a database, or use them in any other way you would use a block device. 

Placed in an Availability Zone (same one as the EC2 instance), where they are automatically replicated for protection from the failure of a single component.

Types (of virutal disks in the cloud):
1. SSD
	- General Purpose SSD (GP2)
	- Provisioned IOPS SSD (IO1) 
		- Highest performance
2. Magnetic
	- Throughput Optimized HDD (ST1)
	- Cold HDD (SC1)
	- Magnetic - _Previous Generation_

## Provision an EC2 Instance
_Build web servers in the cloud._

It's not serverless, it's an actual server in the cloud.

### Common Ports (How Computers Communicate)
Linux = SSH
(Port 22)

Microsoft = Remote Desktop Protocol (RDP)
(Port 3389)

HTTP = Port 80
HTTPS = Port 443 

### Key Pair
How we log into our EC2 instances.

You can have many copies of the padlock, and a key to unlock it.
1. Public Keys
	- many keys can unlock the padlock
2. Private Keys 
	- only one key can unlock the padlock (this is what you use to connect to EC2)

### Security Group
Virtual firewalls in the cloud. You need to open ports in order to use them. 
To let everything in: 0.0.0.0/0
To let just one IP in: X.X.X.X/32

### Launch Instance
Download your private key. 

From the Terminal, navigate to Downloads and change the permissions for your private key:
`chmod 400 MyPrivateKey.pem`

Then SSH into your instance:
`ssh ec2-user@3.81.122.72` 

Note: `3.81.122.72` will be the IP address generated after you have launched your instance. You can find the key _IPv4 Public IP_ in the Description of your instance, then copy the IP address to your clipboard.

To become the root user:
`sudo su`

Update your EC2 instance with the latest security patches.
`yum update -y`

### Design for Failure
Have one instance in each availability zone.


'































 














































































































 
