 # Day 3 – AWS Global Infrastructure Overview
  Today’s focus in the AWS Academy Cloud Foundations course was all about understanding 
  the AWS Global Infrastructure — the physical and regional foundation that powers the cloud

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 - **Topics:**
     - AWS Global Infrastructure
     - AWS service and service category overview

 - **Demo :**  AWS Global Infrastructure

- **Hands-on Activity :**  AWS Management Console clickthrough

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Section 1: AWS Global Infrastructure:
The AWS Global Infrastructure is designed and built to deliver a flexible, reliable, scalable, and secure cloud computing environment with high-quality global network performance.

Educator-Led Demo: AWS Global Infrastructure Details:

The educator might now choose to conduct a live demonstration of the AWS Global Infrastructure map introduced on the previous slide.
This resource provides an interactive way to learn about the AWS Global Infrastructure. The remaining slides in this section cover many of the same topics and go into greater detail on some topics.

**AWS Regions:**
 - An AWSRegionis a geographical area.
 - Data replication across Regions is controlled by you.
 - Communicationbetween Regions uses AWS backbone network infrastructure.
 - Each Region provides full redundancy and connectivity to the network.
 - A Region typically consists of two or more Availability Zones
   
The AWS Cloud infrastructure is built around Regions. AWS has 22 Regions worldwide. 

An AWS Regionis a physical geographical location with one or more Availability Zones. Availability Zones in turn consist of one or more data centers.

Selecting a Region :

Determine the right Region for your services, applications, and data based on these factors
  - Data governance, legal requirements
  - Proximity to customers (latency)
  - Services available within the Region
  - Costs (vary by Region)

**Availability Zones :**

Each AWS Region has multiple, isolated locations that are known asAvailability Zones. 

Each Availability Zone provides the ability to operate applications and databases that are more highly available, fault-tolerant, and scalable than would be possible with a single data center. 

Each Availability Zone can include multiple data centers (typically three), and at full-scale, they can include hundreds of thousands of servers. 

They are fully isolated partitions of the AWS Global Infrastructure. Availability Zones have their own power infrastructure, and they are physically separated by many kilometers from other Availability Zones—though all Availability Zones are within 100 km of each other.

All Availability Zones are interconnected with high-bandwidth, low-latency networking over fully redundant, dedicated fiber that provides high-throughput between Availability Zones. The network accomplishes synchronous replication between Availability Zones.


**AWS data centers :**
    - AWS data centers are designed for security.
    - Data centers are where the data resides and data processing occurs.
    - Each data center has redundant power, networking, and connectivity, and is housed in a separate facility.
    - A data center typically has 50,000 to 80,000 physical servers.

**AWS infrastructure features :**

Now we have a good understanding of the major components that comprise the AWS Global Infrastructure, let's consider the benefits provided by this infrastructure.

The AWS Global Infrastructure has several valuable features:
    - First, it is elasticand scalable. This means resources can dynamically adjust to increases or decreases in capacity requirements. It can also rapidly adjust to accommodate growth.
    - Second, this infrastructure is fault tolerant, which means it has built-in component redundancy which enables it to continue operations despite a failed component.
    - Finally, it requires minimal to no human intervention, while providing high availability with minimal down time


## Section 2: AWS services and service category overview :
AWS offers a broad set of global cloud-based products that can be used as building blocks for common cloud architectures. 

Here is a look at how these cloud based products are organized.

### **AWS foundational services :**
The AWS Global Infrastructure is built on three key elements: Regions, Availability Zones, and Points of Presence (edge locations). This global setup supports a wide range of on-demand services—including compute, networking, storage, and databases—with pay-as-you-go pricing and rapid provisioning.

A typical AWS service stack includes:
    - Infrastructure Layer: Regions, Availability Zones, and Edge Locations
    - Foundational Services: Compute, Networking, Storage
    - Platform Services: Databases, Analytics, App Services, Deployment & Management, Mobile
    - Application Layer: Virtual Desktops, Collaboration & Sharing Tools
    
This layered architecture ensures high availability, scalability, and global accessibility for users and applications.


### **AWS categories of services :**
AWS offers 23 product categories, each containing multiple services. This course focuses only on the most widely used and introductory services, especially those relevant to the AWS Certified Cloud Practitioner exam.
The key service categories covered are:
    - Compute
    - Cost Management
    - Database
    - Management & Governance
    - Networking & Content Delivery
    - Security, Identity & Compliance
    - Storage
    
Each AWS product is organized under these categories. For example, Amazon EC2 falls under Compute. You can explore all services at aws.amazon.com/products.


### Storage service category :
AWS offers several key storage services, each designed for specific use cases:
    - **Amazon S3**: Scalable object storage with high availability, security, and performance. Ideal for websites, mobile apps, backups, IoT data, and big data analytics.
    - **Amazon EBS**: Block storage optimized for use with EC2 instances. Supports high-performance workloads like databases, enterprise and containerized apps, and media workflows.
    - **Amazon EFS**: Elastic file storage (NFS) that automatically scales with usage. Suitable for shared file storage across AWS and on-premises systems.
    - **Amazon S3 Glacier**: Low-cost archival storage for long-term backup. Offers 99.999999999% (11 9s) durability and strong compliance and security features.


### Compute service category :
    - AWS compute services include the services listed here, and many others. 
    - **Amazon Elastic Compute Cloud (Amazon EC2)** provides resizable compute capacity as virtual machines in the cloud. 
    - **Amazon EC2 Auto Scaling** enables you to automatically add or remove EC2 instances according to conditions that you define. 
    - **Amazon Elastic Container Service (Amazon ECS)** is a highly scalable, high performance container orchestration service that supports Docker containers. 
    - **Amazon Elastic Container Registry (Amazon ECR)** is a fully managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images. 
    - AWS Elastic Beanstalk is a service for deploying and scaling web applications and services on familiar servers such as Apache and Microsoft Internet Information Services (IIS). 
    - AWS Lambda enables you to run code without provisioning or managing servers. You pay only for the compute time that you consume. There is no charge when your code is not running.
    - Amazon Elastic Kubernetes Service (Amazon EKS)  makes it easy to deploy, manage, and scale containerized applications that use Kubernetes on AWS.
    - AWS Fargate is a compute engine for Amazon ECS that allows you to run containers without having to manage servers or clusters.

### Database service category :
AWS provides a range of database services for different data needs:
    - **Amazon RDS**: Managed relational database service that simplifies setup, operation, and scaling. Automates backups, patching, and maintenance.
    - **Amazon Aurora**: High-performance relational database compatible with MySQL and PostgreSQL. Up to 5x faster than standard MySQL and 3x faster than PostgreSQL.
    - **Amazon Redshift**: Data warehouse solution optimized for analytics on petabytes of data, including integration with Amazon S3 for querying exabytes of data.
    - **Amazon DynamoDB**: Fully managed NoSQL database (key-value and document-based) with single-digit millisecond performance, built-in security, backup, and in-memory caching.



### Networking and content delivery service category:
AWS offers a variety of networking and content delivery services to ensure secure, fast, and reliable connectivity:
    - **Amazon VPC**: Creates isolated networks in the AWS Cloud for secure resource deployment.
    - **Elastic Load Balancing (ELB)**: Distributes incoming traffic across EC2 instances, containers, IPs, or Lambda functions for high availability.
    - **Amazon CloudFront**: A content delivery network (CDN) that delivers data and applications globally with low latency and high speed.
    - **AWS Transit Gateway**: Connects multiple VPCs and on-premises networks through a central gateway.
    - **Amazon Route 53**: A scalable DNS service that routes users to internet applications by translating domain names into IP addresses.
    - **AWS Direct Connect**: Establishes a dedicated private network connection from your data center to AWS for improved performance.
    - **AWS VPN**: Provides a secure tunnel between your network or device and the AWS global infrastructure


### Security, identity, and compliance service category:
AWS offers a range of security, identity, and compliance services to help protect your applications and data:
    • AWS IAM (Identity and Access Management): Manage users, groups, and permissions to securely control access to AWS resources.
    • AWS Organizations: Centrally manage multiple AWS accounts and apply policies to control service and action permissions.
    • Amazon Cognito: Add user sign-up, sign-in, and access control to web and mobile apps.
    • AWS Artifact: Provides on-demand access to compliance reports and agreements for audits and security documentation.
    • AWS Key Management Service (KMS): Create and manage encryption keys to protect data across AWS services and applications.
    • AWS Shield: Managed DDoS protection for safeguarding applications from attacks.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

AWS cost management service category :
AWS provides several cost management services to help monitor and control spending:
    • AWS Cost and Usage Report: Offers the most detailed data on costs and usage, including metadata on services, pricing, and reservations.
    • AWS Budgets: Lets you set custom budgets and receive alerts when actual or forecasted costs exceed your defined limits.
    • AWS Cost Explorer: A visual tool to analyze and manage your AWS spending over time with easy-to-understand graphs and reports.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Management and governance service category:
    • AWS management and governance services include the services listed here, and others.
    • The AWS Management Console provides a web-based user interface for accessing your AWS account.
    • AWS Config provides a service that helps you track resource inventory and changes.
    • Amazon CloudWatch allows you to monitor resources and applications.
    • AWS Auto Scaling provides features that allow you to scale multiple resources to meet demand.
    • AWS Command Line Interface provides a unified tool to manage AWS services.
    • AWS Trusted Advisor helps you optimize performance and security.
    • AWS Well-Architected Tool provides help in reviewing and improving your workloads.
    • AWS CloudTrail tracks user activity and API usage.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


Hands-on activity:  AWS Management Console clickthrough
1.Launch the Sandboxhands-on environment and connect to the AWS Management Console.
2.Explore the AWS Management Console. 
    A.Click the Servicesmenu. 
    B.Notice how services are grouped into service categories. 
    For example, the EC2service appears in the Computeservice category.

Question #1: Under which service category does the IAM service appear? 
Question #2: Under which service category does the AmazonVPCservice appear?

    C.Click the AmazonVPCservice. Notice that the dropdown menu in the top-right corner displays an AWS Region (for example, it might display N. Virginia). 
    D.Click the Region menu and switch to a different Region. For example, choose EU (London).
    E.Click Subnets(on the left side of the screen). The Region has three subnets in it. Click the box next to one of the subnets. Notice that the bottom half of the screen now displays details about this subnet. 

Question #3: Does the subnet you selected exist at the level of the Region or at the level of the Availability Zone?

    F.Click Your VPCs. An existing VPC is already selected. 

Question #4: Does the VPC exist at the level of the Region or the level of the Availability Zone?
Question #5: Which services are global instead of Regional?  Check Amazon EC2, IAM, Lambda, and Route 53

Answer :
# Activity Steps & Answers

# 1. Launch and Access Console
- Opened the AWS Sandbox environment.
- Accessed the [AWS Management Console](https://aws.amazon.com/console/).

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 2. Services Menu Observations
- Clicked the **Services** menu.
- Observed how services are grouped by category.

#❓ Question 1: Under which service category does the **IAM** service appear?
    --> Security, Identity, and Compliance

#❓ Question 2: Under which service category does the **Amazon VPC** service appear? 
    --> Networking & Content Delivery

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 3. Region & Subnet Inspection
- Selected **Amazon VPC**.
- Checked the top-right to find the current AWS Region (e.g., N. Virginia).
- Changed Region to **EU (London)**.

# Navigated to Subnets:
- Clicked **Subnets** from the left menu.
- Selected a subnet and reviewed the details displayed.

#❓ Question 3: Does the subnet exist at the level of the Region or Availability Zone?
   --> Availability Zone

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 4. VPC Configuration
- Clicked **Your VPCs**.
- Viewed existing VPC details.

#❓ Question 4: Does the VPC exist at the level of the Region or the Availability Zone?
   --> Region

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# 5. Global vs. Regional Services

Checked the scope of the following services:

Service	   Scope
EC2	        Regional
IAM	        Global
Lambda	     Regional
Route 53	   Global


#❓ Question 5: Which services are global instead of Regional?
   --> IAM and Route 53

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


# ✅ Activity Completed
This hands-on activity helped in understanding:
- AWS service groupings
- Regional and AZ-level resource management
- Global vs Regional service scope in AWS

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------





