# Module 6: Compute
## Topics
- Compute services overview
- Amazon EC2
- Amazon EC2 cost optimization
- Container services
- Introduction to AWS Lambda
- Introduction to AWS Elastic Beanstalk
## Demo
- Recorded demonstration of Amazon EC2Lab
- Introduction to Amazon EC2
## Lab
- Introduction to Amazon EC2

## Section 1: AWS Compute services overview
-	Amazon EC2: Resizable virtual machines.
-	EC2 Auto Scaling: Automatically adds/removes EC2 instances based on demand.
-	Amazon ECR: Stores and retrieves Docker container images.
-	Amazon ECS: Orchestrates Docker containers.
-	Amazon EKS: Managed Kubernetes service.
-	AWS Fargate: Run containers without managing servers.
-	AWS Lambda: Serverless compute; pay per use.
- AWS Elastic Beanstalk: Run and manage web apps easily.
-	Amazon Lightsail: Simplified VM service for apps/websites.
-	AWS Batch: Run large-scale batch computing jobs.
-	VMware Cloud on AWS: Run VMware-based workloads on AWS.
-	AWS Outposts: Run AWS services on-premises.
-	Serverless Application Repository: Find and deploy serverless apps.

### Categorizing compute services

AWS Compute Services – 4 Broad Categories

AWS compute offerings can be grouped into four main categories based on how much control you need over infrastructure and how your applications are built:

**1. Virtual Machines (IaaS – Infrastructure as a Service)**
-	Amazon EC2 provides scalable virtual machines where you manage the OS, runtime, and application.
-	You choose the operating system, CPU, memory, storage, and networking.
-	This approach offers maximum flexibility, similar to on-premises infrastructure.
-	Ideal for IT professionals who are used to traditional servers.
-	EC2 is one of AWS’s oldest and most widely used services.
**2. Serverless Computing**
-	AWS Lambda lets you run code without provisioning or managing servers.
-	You simply upload your code and define when it should run (event-driven).
-	You only pay for the compute time used, not for idle time.
-	Great for modern cloud-native applications with dynamic workloads.
-	While it's newer, it's quickly gaining popularity due to scalability and cost efficiency.
**3. Container-Based Services**
 	
Containers let you package applications with their dependencies to run consistently across environments.
They are faster to launch than VMs and use fewer resources.

Key AWS services in this category include:
-	Amazon ECS (Elastic Container Service) – AWS’s own container orchestration service.
-	Amazon EKS (Elastic Kubernetes Service) – Managed Kubernetes environment.
-	AWS Fargate – Run containers without managing servers or clusters.
-	Amazon ECR (Elastic Container Registry) – Stores and manages container images.

Container-based architecture is popular for microservices and CI/CD pipelines.

**4. Platform as a Service (PaaS)**
-	AWS Elastic Beanstalk is a PaaS solution that lets you deploy and scale web applications quickly.
-	AWS automatically handles provisioning, load balancing, scaling, and monitoring.
-	You just upload your code; AWS handles the OS, runtime, and infrastructure.
-	Ideal for developers who want to focus on writing code without managing environments.





## Section 2: Amazon EC2

**Amazon EC2 – A Cost-Effective Alternative to On-Premises Servers**
Running servers on-premises is costly due to the need for purchasing hardware, building and maintaining data centers, and provisioning for peak traffic—even if that capacity sits idle most of the time. 

This leads to wasted resources and high overhead.
Amazon EC2 offers a flexible alternative by providing secure, resizable virtual machines in the cloud, allowing you to run the same applications as on physical servers—without upfront hardware costs or long-term commitments.
Common EC2 use cases include:
-	Web and application servers
-	Database and media servers
-	Game and mail servers
-	File, proxy, and catalog servers
-	General compute workloads


**Launching an Amazon EC2 Instance** – Getting Started

When we launch an EC2 instance for the first time, you’ll likely use the AWS Management Console’s Launch Instance Wizard. 

This tool simplifies the process—if you go with default settings, you can launch an instance in as few as six clicks.

We'll get hands-on experience with this in the lab provided in the module.

While the wizard is quick and easy, most real-world deployments require customizing settings to meet specific needs.

The upcoming slides will guide you through the key configuration choices during the EC2 launch process and explain the concepts behind each option, helping you make informed decisions.

### Step 1: Select an Amazon Machine Image (AMI)

An Amazon Machine Image (AMI) contains the necessary information to launch an EC2 instance, such as the operating system, pre-installed software, and configurations.

You must choose an AMI when launching an instance.
-	You can use different AMIs for different roles, like web servers or app servers.
-	You can also launch multiple instances from a single AMI.
Each AMI includes:
-	A template for the root volume (usually includes the OS and software).
-	Launch permissions (who can use the AMI).
-	Block device mapping (specifies attached volumes).
AMI options include:
-	Quick Start: Pre-built AMIs from AWS (Linux, Windows).
-	My AMIs: Custom AMIs you’ve created.
-	AWS Marketplace: AMIs with commercial software from vendors.
-	Community AMIs: Publicly shared AMIs from users—use with caution, especially in production environments.

**Creating a New AMI – Example**

An AMI (Amazon Machine Image) can be created from an existing EC2 instance, whether it was imported or launched from a base AMI.

Steps to create a custom AMI:

**1.	Start with a base instance :**

Launch an EC2 instance using a Quick Start AMI or by importing your own virtual machine. This creates an unmodified instance.

**2.	Customize the instance :**

Configure it with the desired OS settings, applications, and tools—this is often called a golden instance.

**3.	Create the AMI :**

Once your instance is ready, you can create a new AMI from it.
-	EC2 stops the instance,
-	Takes a snapshot of the root volume,
-	And registers it as an AMI.
  
**4.	Reuse and share :**

-	The new AMI can now be used to launch identical instances in the same Region.
-	You can also copy the AMI to other Regions to support deployments across different geographies.

### Step 2: Select an Instance Type

After selecting an AMI, the next step is to choose an instance type—which defines the hardware of your EC2 instance.

Amazon EC2 offers a wide range of instance types, each optimized for different use cases.

Instance types vary in CPU, memory, storage, and networking capacity, allowing you to choose the right mix of resources for your workload.

Each type also comes in multiple sizes, so you can scale up or down based on your needs.

Main instance type categories:
-	General Purpose – Balanced for a variety of workloads (e.g., t4g, t3, m6i).
-	Compute Optimized – High-performance CPUs for compute-intensive tasks.
-	Memory Optimized – Ideal for memory-heavy applications (e.g., databases, analytics).
-	Storage Optimized – Designed for high disk throughput and IOPS.
-	Accelerated Computing – Includes GPUs or FPGAs for specialized processing (e.g., ML, graphics).


### EC2 Instance Type Naming and Sizes
EC2 instance names follow a structured format that helps you understand their capabilities:

Example: t3.large
-	T – The instance family (T = General Purpose).
-	3 – The generation number (higher = newer and better performance).
-	large – The size, which affects vCPU, memory, and network performance.

Size Comparison:

Each size is a multiple of resources:
-	t3.large
-	t3.xlarge = 2× t3.large
-	t3.2xlarge = 2× t3.xlarge

As size increases, so do:
-	vCPUs
-	Memory
-	Network bandwidth

### Selecting an EC2 Instance Type by Use Case
EC2 instance types differ by CPU, core count, memory, storage, and network performance. Based on your workload, choose an instance family that best fits your needs.

Here are some common examples:
-	T3 (General Purpose, Burstable)
  -	Offers baseline CPU with the ability to burst when needed.
  -	Use cases: Websites, dev/test environments, build servers, microservices, and business apps.
-	C5 (Compute Optimized)
  -	Designed for high-performance, compute-heavy tasks at low cost per compute.
  -	Use cases: Scientific modeling, batch jobs, multiplayer gaming, ad serving, and video encoding.
-	R5 (Memory Optimized)
  -	Ideal for memory-intensive workloads with large data sets.
  -	Use cases: High-performance databases, data analytics, in-memory caching, big data processing (e.g., Hadoop, Spark).

🔗 For a full list of EC2 instance types and specs, visit: AWS EC2 Instance Types




### Step 3: Specify Network Settings
After selecting an AMI and instance type, choose the network where your EC2 instance will run.
-	First, select the correct AWS Region before starting the Launch Instance Wizard. Your instance will be deployed in that Region.
-	Next, choose a VPC (Virtual Private Cloud) and subnet:
  -	Default VPC: Instances are automatically assigned a public IPv4 address.
  -	Nondefault VPC: By default, no public IP is assigned.
You can control public IP assignment by:
-	Changing the subnet’s IP settings, or
-	Overriding it manually during launch by enabling/disabling public IP.
Choosing the right network settings ensures your instance is reachable (e.g., from the internet) if needed

### Step 6: Specify Storage
When launching an EC2 instance, you can configure the instance's storage settings:
-	Root volume:
Contains the operating system and is created from the selected AMI. You can adjust its size and volume type.
-	Additional volumes:
You can attach extra storage at launch for data or applications. Some AMIs include extra volumes by default.

For each volume, you can specify:
-	Size (in GiB)
-	Volume type (e.g., General Purpose SSD, Provisioned IOPS)
-	Delete on termination (whether the volume is deleted when the instance is stopped/terminated)
-	Encryption (for secure data storage)

Proper storage configuration is important for performance, data retention, and security.

### Step 7: Add Tags
Tags are labels you assign to AWS resources like EC2 instances to help with organization, management, and automation.
-	Each tag is a key-value pair (e.g., Key: Name, Value: MyWebServer)
-	Tags help you categorize by environment, owner, department, purpose, etc.
-	Tags are case-sensitive: Name (with capital "N") is shown in the EC2 console's Name column, but name (lowercase) is not.
 Best Practices:
-	Use consistent naming (e.g., Environment: Production, Owner: Gauraj)
-	Develop a tagging strategy across your organization
-	Tags help in searching, filtering, and even cost allocation

🔗 For more, see: AWS Tagging Best Practices (PDF)

**Some key takeaways from this section of the module include:**
- Amazon EC2 enables you to run Windows and Linux virtual machines in the cloud.
- You launch EC2 instances from an AMI template into a VPC in your account.
- You can choose from many instance types. Each instance type offers different combinations of CPU, RAM, storage, and networking capabilities.
- You can configure security groups to control access to instances (specify allowed ports and source).
- User data enables you to specify a script to run the first time that an instance launches. 
- Only instances that are backed by Amazon EBS can be stopped. 
- You can use Amazon CloudWatch to capture and review metrics on EC2 instances

## Section 3: Amazon EC2 cost optimization
### Amazon EC2 Pricing Models

AWS offers several pricing options to suit different workloads and budgets:
- 1.	On-Demand Instances
  -	Pay-as-you-go, no long-term commitment
  -	Ideal for short-term, unpredictable workloads
  -	Eligible for AWS Free Tier
  -	Billed per second (Amazon Linux/Ubuntu only)
- 2.	Reserved Instances (RI)
  -	Commit to 1 or 3 years for lower hourly rates
  -	Best for steady, long-term workloads
  -	Cost-effective for predictable usage
- 3.	Scheduled Reserved Instances
  -	Reserve instances for specific recurring times (daily/weekly/monthly)
  -	Pay for scheduled time even if unused
- 4.	Spot Instances
  -	Bid on unused EC2 capacity at up to 90% discount
  -	Ideal for flexible, fault-tolerant workloads
  -	Can be interrupted by AWS when capacity is needed
- 5.	Dedicated Hosts
  -	Entire physical server reserved for your use
  -	Use your own software licenses (e.g., Windows, SQL Server)
  -	Suitable for regulatory/compliance requirements
- 6.	Dedicated Instances
  -	Run in VPC on hardware dedicated to your account
  -	Physically isolated from other customers' instances

**Amazon EC2 Pricing Models: Benefits**
-	On-Demand Instances
  -	Most flexible: no upfront payment or long-term commitment
  -	Great for short-term or unpredictable workloads
-	Spot Instances
  -	Up to 90% cheaper than On-Demand
  - Ideal for large-scale, flexible, or fault-tolerant applications
-	Reserved Instances
  -	Lower cost for consistent, long-term usage (1 or 3 years)
  -	Best for steady-state workloads (e.g., databases, backend services)
-	Dedicated Hosts
  -	Physical server dedicated to your use
  -	Perfect for BYOL (Bring Your Own License) and meeting compliance needs
### The Four Pillars of Cost Optimization
- 1.	Right-size
  -	Choose the appropriate instance types and sizes.
  -	Scale down or shut off unused servers.
-2.	Increase Elasticity
  -	Use Auto Scaling to match resources with demand.
  -	Avoid paying for idle capacity.
-3.	Use Optimal Pricing Models
  -	Mix On-Demand, Reserved, and Spot Instances based on usage patterns.
-4.	Optimize Storage
  -  Delete unused volumes.
  -	Choose cost-effective storage that meets performance needs.


## Section 4: Container services
### Container Basics
-	Containers use OS-level virtualization to run applications and their dependencies in isolated environments.
-	They package code, configuration, libraries, system tools, and the runtime into a single, lightweight unit.
-	Unlike virtual machines, containers do not include a full OS—they share the host OS kernel, making them faster and smaller.
-	Benefits of Containers:
  -	Environmental consistency across development, testing, and production.
  -	Quick startup: Containers launch in milliseconds.
  -	Lightweight: Significantly smaller than VMs in size.
  -	Portability: Can run on any infrastructure—on-premises, cloud, or hybrid.
  -	Operational efficiency: More granular resource control and better infrastructure utilization.
  -	Improved DevOps productivity and better version control for deployments.

### What is Docker?
Docker is a software platform that enables developers to package applications and their dependencies into containers—lightweight, portable units of software that can run consistently across various environments

**Why Use Docker?**

Docker helps you:
-	 Standardize environments – Avoid issues like “it works on my machine.”
-	 Reduce conflicts – Isolate language stacks, libraries, and versions.
-	 Use Containers as a Service (CaaS) – Easily manage, scale, and orchestrate containers.
-	 Support microservices – Package each service independently for modular deployments.
-	 Achieve portability – Seamlessly move containerized applications between environments (dev, test, prod, cloud, on-prem).

**How Docker Works:**
-	Docker runs on every host machine and provides CLI tools to:
  -	Build container images
  -	Start or stop containers
  -	Share and reuse container images

### Amazon Elastic Container Service (Amazon ECS)
Amazon ECS is a fully managed container orchestration service that simplifies running and managing Docker containers.

Instead of manually setting up EC2 instances with Docker, ECS handles:
- Launching thousands of containers in seconds
- Monitoring deployments
- Managing cluster state
- Scheduling containers (built-in or third-party like Apache Mesos, Blox)

ECS supports Spot and Reserved Instances for cost optimization.

### Amazon ECS orchestrates containers
In Amazon ECS, a task definition is a blueprint that defines one or more containers (up to 10) for your application, including settings like container images, ports, and volumes.

A task is a running instance of this definition on an ECS cluster (a group of EC2 instances with the ECS agent). ECS uses a scheduler to place tasks on cluster instances based on available resources like CPU and memory.

### What is Kubernetes?
Kubernetes is an open-source platform for orchestrating containers—including Docker—at scale. It allows you to deploy, manage, and scale containerized applications across clusters of compute nodes.

Key features:
-	Runs containers in pods (logical groups).
- Assigns each pod an IP and DNS for internal/external communication.
-	Works across on-premises and cloud environments.
-	Supports auto-scaling, self-healing, and load balancing.
-	Backed by a large open-source community with frequent updates.

### Amazon Elastic Kubernetes Service (Amazon EKS)
Amazon EKS is a fully managed Kubernetes service that lets you run Kubernetes on AWS without installing or managing the Kubernetes control plane yourself.

Features:
-	Fully Kubernetes-conformant (compatible with upstream Kubernetes).
-	Handles cluster availability, scaling, and automatic health monitoring.
-	Integrates with AWS tools like IAM, VPC, and Application Load Balancer.
-	Offers high performance, reliability, and security using AWS infrastructure.

### Why EKS if ECS exists?
AWS provides both ECS and EKS to give you flexibility—choose ECS for AWS-native orchestration or EKS if you want to use standard Kubernetes.

### Amazon Elastic Container Registry (Amazon ECR)
Amazon ECR is a fully managed Docker container registry that helps you store, manage, and deploy container images easily.

**Key Features:**
-	Integrated with Amazon ECS and EKS for seamless image deployment.
-	Supports Docker CLI and tools via Docker Registry HTTP API v2.
-	Accessible from any environment—cloud, on-premises, or local.
- Transfers images via HTTPS and encrypts them at rest using Amazon S3.

**Use Case:**

Store your container images in ECR, link them in your ECS/EKS task definitions, and let AWS handle the rest.


### Section 5: Introduction to AWS Lambda
### AWS Lambda: Run Code Without Servers
AWS Lambda is a serverless, event-driven compute service that lets you run code without provisioning or managing servers.

**How it works:**

-	You upload your code as a Lambda function.
-	It runs only when triggered (e.g., by events or schedules).
-	You pay only for the compute time used—no charges when your code isn’t running.

**Benefits:**
-	No server management
-	Scales automatically
-	Cost-effective for event-based or intermittent workloads

### Benefits of AWS Lambda
-	No infrastructure management
  - AWS handles server provisioning, maintenance, scaling, and fault tolerance automatically.
-	Supports popular languages
  - Works with Java, Python, Node.js, C#, Go, PowerShell, Ruby, and more.
-	Use any libraries
  - Native and third-party libraries are supported.
-	Built-in logging & monitoring
  - Integrated with Amazon CloudWatch for visibility.
-	Fault tolerant by design
  - Runs across multiple Availability Zones (AZs) for high availability.
-	Scales automatically
  - Handles from a few to thousands of requests per second with no manual scaling.
-	Cost-effective
  - Pay only for execution time (billed in 100ms increments).
-	Supports orchestration
  - Integrate with AWS Step Functions for building complex workflows.

Schedule-based Lambda Example: EC2 Start & Stop

Goal: Automatically stop EC2 instances at night and start them in the morning to save costs.

**How It Works:**
- 1.	CloudWatch Event (22:00 GMT)
  - Triggers a Lambda function to stop EC2 instances.
- 2.	Lambda Function Executes
  - Uses an IAM role with permission to stop instances.
- 3.	EC2 Instances Stopped
- 4.	CloudWatch Event (05:00 GMT)
  - Triggers another Lambda function to start EC2 instances.
- 5.	Lambda Function Executes
  - Uses an IAM role with permission to start instances.
- 6.	EC2 Instances Started
**Benefits:**
-	Automates instance lifecycle
-	Saves cost during idle hours
-	Requires no manual intervention

### AWS Lambda Quotas (Limits)
-	Memory: Up to 10,240 MB per function
-	Timeout: Max 15 minutes per function run
-	Concurrent executions: Default limit of 1,000 per Region
-	Deployment package size:
  -	ZIP: 250 MB (uncompressed)
  -	Container image: Up to 10 GB
-	Layers: Reusable ZIPs for dependencies — helps reduce deployment size
-	Limits:
  -	Soft limits: Can be increased via AWS Support
  -	Hard limits: Cannot be increased

 For the most up-to-date limits, refer: AWS Lambda Quotas Documentation

## Section 6: Introduction to AWS Elastic Beanstalk
### AWS Elastic Beanstalk – Quick Overview
**What it is:**

A Platform as a Service (PaaS) that simplifies deploying, scaling, and managing web applications and services.

**Key Features:**
-	Just upload your code, and Beanstalk handles:
  -	Deployment
  -	Capacity provisioning
  -	Load balancing
  -	Auto scaling
  -	Monitoring health
-	Supports full control over underlying AWS resources (EC2, S3, etc.)
-	Choose your instance type, database, and configure settings like HTTPS, logs, etc.

Pricing:
No extra cost for Elastic Beanstalk itself —
You only pay for the AWS resources you use (like EC2, RDS, S3).

### AWS Elastic Beanstalk – Deployments
**How to deploy:**

Use any of the following:
-	AWS Management Console
-	AWS CLI
-	Visual Studio
-	Eclipse

**What we need:** Just write the code – Beanstalk handles everything else.

**Supported Platforms:**
-	Languages: Java, .NET, Node.js, Python, PHP, Go, Ruby, Docker
-	Web servers/environments:
  -	Java → Apache Tomcat
  -	PHP/Python → Apache HTTP Server
  -	Node.js → NGINX / Apache
  -	Ruby → Passenger / Puma
  -	.NET → IIS
  -	Go/Docker → Native support
- Goal: Fast and easy application deployment with minimal setup.

**Benefits of AWS Elastic Beanstalk**
-	Easy to start:

Deploy apps quickly via the AWS Console, Git, or IDEs like Eclipse & Visual Studio.
-	Fully managed infrastructure:
  
Automatically handles deployment, load balancing, scaling, and monitoring.
-	Developer-friendly:
  
Focus on coding—no need to manage servers, firewalls, or networking.
-	Automatic updates:
  
AWS applies patches and platform updates for you.
- Scalable:
  
Handles traffic spikes using auto scaling based on metrics like CPU utilization.
-	Customizable:
  
Choose your own EC2 instance types and AWS resources.
-	Full control:
  
Easily take over infrastructure management whenever needed.

## Lab 3: Introduction to Amazon EC2
**Introduction to Amazon EC2.**

**This lab provides hands-on practice with launching, resizing, managing, and monitoring an Amazon EC2 instance.**

**In this lab, I have launch and configure my first virtual machine that runs on Amazon EC2**

**In this hands on lab, completed the tasks:**
- Launched my Amazon EC2 Instance
- Monitored that Instance
- Updated Security Group and Accessed the Web Server
- Resize Instance: Instance Type and EBS Volume
- Explored EC2 Limits
•Test Termination Protection

