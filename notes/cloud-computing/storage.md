## Storage Options

### S3
Provides simple object storage, useful for hosting static websites, images and videos, data analytics, mobile and web applications. 
* No hierarchy of relations between files with object storage.
* Data objects can be distributed across several machines. 
* S3 is accessible from anywhere on the internet. 

### EBS
Provides persistent block-level data storage. 
* Block storage stores files in multiple volumes called blocks, which act as separate hard drives; block storage devices are more flexible and offer higher performance than regular file storage. 
* Need to mount EBS onto an EC2 Instance.
* Use cases: business continuity, software testing, database management.

### EFS
A shared, elastic file storage system that grows and shrinks as you add and remove files.
* Offers a traditional file storage paradigm, with data organized into directories and subdirectories. 
* Can mount EFS onto several EC2 instances at the same time.
* Use cases: Big Data and analytics, media processing workflows, content management, web serving, and home directories.


### When should I use S3 vs. EBS vs. EFS? 
S3 is an object storage service. S3 makes data available through an Internet API that can be accessed anywhere.

EBS is a block level storage service for use with EC2. EBS can deliver performance for workloads that require the lowest-latency (minimal delay) access to data from a single EC2 instance. 

Amazon EFS is a file storage service for use with EC2. EFS provides a file system interface, file system access semantics (such as strong consistency and file locking) and concurrently-accessible storage for up to thousands of EC2 instances. 


