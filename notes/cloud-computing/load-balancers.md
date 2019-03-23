## Load Balancers
Automatically distributes incoming application traffic across multiple targets, such as EC2 instances, containers, IP addresses, and Lambda functions. It can handle the varying load of your application traffic in a single Availability Zone or across multiple Availability Zones. 

Elastic Load Balancing offers three types of load balancers that all feature the high availability, automatic scaling, and robust security necessary to make applications fault tolerant.

### Application Load Balancer (ALB)
Best suited for load balancing of HTTP and HTTPS traffic. Provides advanced request routing targeted at the delivery of modern arhitectures, including microservices and containers. Operating at the individual request level (Layer 7), Application Load Balancer routes traffic to targets within Amazon Virtual Private CLoud (VPC) based on the content of the request.

### Network Load Balancer
Best suited for load balancing of Transmission Control Protocol (TCP) and Transport Layer Security (TLS) traffic where extreme performance is required. Operating at the connection level (Layer 4), Network Load Balancer routes traffic to targets within Amazon Virtual Private Cloud (VPC) and is capable of ahndling millions of requests per second while maintaining ultra-low latencies. Also optimized to handle suddent and volatile traffic patterns.

### Classic Load Balancer
Provides basic load balancing across multiple EC2 Instances and operates at both the request level and connection level. Intended for applications that were build within the EC2-Classic network.

## Auto Scaling
You can maintain application availability and scale your EC2, DynamoDB, ECS, Elastic Container Service for Kubernetes (EKS) capacity up or down automatically according to the conditions you define.

You can use Auto Scaling to help make sure that you are running the desired number of healthy EC2 instances across multiple Availability Zones. Auto Scaling can also automatically increase the number of EC2 instances during demand spikes to maintain performance and decrease capacity during less busy periods to optimize costs.
