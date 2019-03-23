# AWS Billing and Pricing

## AWS Pricing White Paper
_Read AWS Pricing Overview whitepaper._

Types of Pricing:
1. Pay as you go
2. Pay less when you reserve
3. Pay even less per unit by using more
4. Pay even less as AWS grows
5. Custom pricing

Three drivers of cost with AWS:
- Compute
- Storage
- Data Outbound

_What services are included in the Free Tier?_
* Amazon VPC (VPC = a virtual data center in the cloud)
* Elastic Beanstalk 
* CloudFormation
* IAM
* Auto Scaling
* Opsworks (similar to Elastic Beanstalk)
* Consolidated Billing

_What determines price?_
* Clock Hours of Server Time
* Instance Type (t2.micro, etc.)
* Pricing Model (spot, on-demand, etc.)
* Number of Instances
* Load Balancing
* Detailed Monitoring 
* Auto Scaling
* Elastic IP Addresses
* Operating Systems and Software Packages

_What determines price for Lambda?_
* Request Pricing
  * Free Tier: 1 million requests per month
  * $0.20 per 1 million requests thereafter
* Duration Pricing
  * Additional Charges (if your Lambda function uses other services, for example)

_What determines price for EBS?_
* Volumes (per GB)
* Snapshots (per GB)
* Data Transfer

_What determines price for S3?_
* Storage Class (Standard, IA, 1 AZ IA, etc.)
* Storage (how much data are you storing)
* Request (GET, PUT COPY)
* Data Transfer

_What determines price for Glacier?_
* Storage
* Data retrieval times

**Snowball** <br>
A PB-scale _data transport solution_ that uses secure applicances to transfer large amounts of data into and out of the AWS cloud.

Think of it as a gigantic disk to move your data into AWS.

_What determines price for Snowball?_
* Service fee per job
* Daily charge
* Data Transfer (data in, free; data out, costs)

_What determines price for RDS?_
* Clock hours of server time
* Database characteristics
* Database purchase type
* Number of database instances
* Provisioned storage
* Additional storage
* Requests
* Deployment Types
* Data Transfers

_What determines price for DynamoDB?_
* Provisioned throughput (write)
* Provisioned throughput (read)
* Indexed data storage

_What determines price for CloudFront?_
* Traffic Distribution
* Requests
* Data Transfer Out

## Support Plans
Basic: Free
Developer: $29/mo (12 hours)
Business: $100/mo (1 hours)
Enterprise: $15,000/mo (15 mins)

Note: Response time based on system impaired or production down.

## Tagging & Resource Groups
**Tags**: key value pairs attached to AWS resources
* Contains metadata (data about data)
* Tags can sometimes be inherited

**Resource groups**: make it easy to group your resources using tags that are assigned to them
* Contain specific information
  * EC2: Public & Private IP Addresses
  * ELB: Port Configurations
  * RDS: Database Engine, etc.

**Tag Editor** (global service) finds and filters tags associated with resources.

## Organizations & Consolidated Billing
AWS Organizations: an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage.

## AWS Calculators
1. AWS Simple Monthly Calculator
	- Running monthly cost
	- https://calculator.s3.amazonaws.com/index.html
2. AWS Total Cost of Ownership Calculator
	- Cost of On-Prem vs. AWS (comparison tool)
	- https://aws.amazon.com/tco-calculator/
	
## Summary
Philosphy: pay as you go, pay for what you use, pay less as you use more, and pay even less when you reserve capacity.

Organization Full Access & Organization Consolidated Billing

Billing Alerts: when monitoring is enabled on the paying account, the billing data for all linked accounts is included.

**CloudTrail**: For auditing.
	- Per AWS account and is enabled per region. 
	- Can consolidate logs using an S3 bucket:
		- Turn on CloudTrail in paying account.
		- Create a bucket policy that allows cross-account access.
		- Turn on CloudTrail in the other accounts and use the bucket in the paying account.

Consolidated billing: allows you to get volume discounts on your accounts.

Quick Start: way of deploying environments quickly using CloudFormation templates built by AWS Solutions Architects who are experts in that particular technology.

AWS Landing Zone: a solution that helps customers more quickly set up a secure, multi-account AWS environment based on AWS best practices.

## Quiz Answers:
- The Developer support plan features access to AWS support explicitly during business hours via email. With the AWS exams you need to be careful of wording. Business and Enterprise offer 24x7 access not just business hours. If you were asked to provide three answers those might be included, but with only 1 answer, you must chose the most precise answer.
- In total there are 9 valid sections allowed within a CloudFormation template. In the answers above, only "Parameters", "Resources" and "Outputs" are considered valid. "Options" is not a template section. 
- A resource group is a collection of resources that share one or more tags (or portions of tags.)
- Consolidated Billing is a feature of AWS Organizations. Once enabled and configured, you will receive a bill containing the costs and charges for all of the AWS accounts within the Organization. Although each of the individual AWS accounts are combined into a single bill, they can still be tracked individually and the cost data can be downloaded in a separate file. Using Consolidated Billing may ultimately reduce the amount you pay, as you may qualify for Volume Discounts. There is no charge for using Consolidated Billing.
- Failover Routing and Latency-based Routing are the only two correct options, as they consider routing data based on whether the resource is healthy or whether one set of resources is more performant than another. Any answer containing location based routing (Geoproximity and Geolocation) cannot be correct in this case, as these types only consider where the client or resources are located before routing the data. They do not take into account whether a resource is online or slow. Simple Routing can also be discounted as it does not take into account the state of the resources.














