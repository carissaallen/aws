## Mega Quiz Solutions

- The Storage Gateway service is primarily used for attaching infrastructure located in a Data centre to the AWS Storage infrastructure. The AWS documentation states that; "You can think of a file gateway as a file system mount on S3." Amazon Elastic File System (EFS) is a mountable file storage service for EC2, but has no connection to S3 which is an object storage service. Amazon Elastic Block Store (EBS) is a block level storage service for use with Amazon EC2 and again has no connection to S3. [Further information.](https://docs.aws.amazon.com/storagegateway/latest/userguide/WhatIsStorageGateway.html)

You have a mission-critical application which must be globally available at all times. Which deployment strategy should you follow?
- A Multi-Region deployment will best ensure global availability.

- A region is a geographical area divided into Availability Zones. Each region contains at least two Availability Zones.

- AWS Organizations is an account management service which allows you manage multiple accounts centrally.

You have been ask to deploy a clustered application on a small number of EC2 instances. The application must be placed across multiple Availability Zones, have high speed, low latency communication between each of the nodes, and should also minimise the chance of underlying hardware failure. Which of the following options would provide this solution?
- Spread Placement Groups are recommended for applications that have a small number of critical instances which need to be kept separate from each other. Launching instances in a Spread Placement Group reduces the risk of simultaneous failures that might occur when instances share the same underlying hardware. Spread Placement Groups provide access to distinct hardware, and are therefore suitable for mixing instance types or launching instances over time. In this case, deploying the EC2 instances in a Spread Placement Group is the only correct option. [Further information](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)

- With S3, objects can be accessed from anywhere in the world via a dedicated URL.

- In both AWS-Budget & CloudWatch alarms can be set to monitor spending on your AWS Account.

- An online resource to help you reduce cost, increase performance, and improve security by optimizing your AWS environment, Trusted Advisor provides real time guidance to help you provision your resources following AWS best practices.

- The customer is responsible for her own customer data.

You are considering moving an on-premise SQL Server cluster into AWS, using EC2 instances rather than RDS. You need to recommend the most suitable EBS volume type for the cluster to use, but also pair it with a suitable EC2 instance type. You know that the throughput must be good, but the most important thing is to maintain a consistent level of IOPS under normal load which can increase to a much higher level at busy times. Choose the best option from the following EC2 and EBS pairings.
- The question states that you require consistent IOPS which means the io1 Provisioned IOPS type is the best choice of the two EBS types available, and therefore the correct answer must have io1 as an option. Of the remaining two answers, either EC2 families would work. We know from experience that databases do utilise as much memory as is available, so choosing an r5 family is plausible, however we need to use our extended knowledge of EC2 families to know that X1e was specifically created to run high performance databases and the final answer will therefore contain an io1 EBS volume and the X1e EC2 option. 
- [EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/)
- [EBS Features](https://aws.amazon.com/ebs/features/)
- [Database](https://aws.amazon.com/blogs/database/new-memory-optimized-amazon-ec2-instance-types-drive-database-workloads/)

- Redshift is AWS' data warehousing service.

- Lambda is the AWS Function-as-a-Service (FaaS) offering that lets you run code without provisioning or managing servers.

- With AWS Organizations, you can use either just the Consolidated Billing feature, or all the offered features.

- Aurora is AWS' managed database service that is up to 5X faster than a traditional MySQL database.

- The number of Edge Locations is greater than the number of Availability Zones, which is greater than the number of Regions.

- All accounts receive billing support.

- Amazon EMR is a web service that makes it easy to process large amounts of data efficiently.

In addition to choosing the correct EBS volume type for your specific task, what else can be done to increase the performance of your volume? (Choose 3)
- There are a number of ways you can optimise performance above that of choosing the correct EBS type. One of the easiest options (and the first option on the list) is to drive more I/O throughput than you can provision for a single EBS volume, by striping using RAID 0. You can join multiple gp2, io1, st1, or sc1 volumes together in a RAID 0 configuration to use the available bandwidth for these instances. The second option is to choose an EC2 instance type that supports EBS optimisation. This ensures that network traffic cannot contend with traffic between your instance and your EBS volumes. The final correct choice is the last option and only relates to HDD based EBS volumes. When you create a snapshot of a Throughput Optimized HDD (st1) or Cold HDD (sc1) volume, performance may drop as far as the volume's baseline value while the snapshot is in progress. This behaviour is specific to these volume types. Therefore you should ensure that scheduled snapshots are carried at times of low usage. The one option on the list which is entirely incorrect is the option that states "Never use HDD volumes, always ensure that SSDs are used" as the question first states "In addition to choosing the correct EBS volume type for your specific task". HDDs may well be suitable to certain tasks and therefore they shouldn't be discounted because they may not have have the highest specification on paper. 
- [EBS Features](https://aws.amazon.com/ebs/features/)
- [EBS Performance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSPerformance.html)

- Build your systems to be scalable, use disposable resources, reduce infrastructure to code, and, please, assume EVERYTHING will fail sooner or later.

- The AWS Database Migrations Service is the best choice for conventional data migrations.
- [DMS](https://aws.amazon.com/dms/)

## Other
[Exam Tips](https://www.shanebart.com/aws-cloud-practitioner/)
[Free Amazon Training](https://aws.amazon.com/training/course-descriptions/cloud-practitioner-essentials/)
[Mock Tests](https://www.udemy.com/aws-cloud-certified-practitioner-mock-tests/?couponCode=AWSCCP777)
[Exam Guide](https://aws.amazon.com/certification/certified-cloud-practitioner/?linkCode=w61&imprToken=ez.gx-rIAq0BQnA4anXtjQ&slotNum=7)
