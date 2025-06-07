# Day 5: Networking and Content Delivery
### Topics
- Networking basics
- Amazon VPC
- VPC networking
- VPC security
- Amazon Route 53 
- Amazon CloudFront
### Activities
- Label a network diagram
- Design a basic VPC architecture
 ### Demo
- VPC demonstration
### Lab
- Build your VPC and launch a web server


## Section 1: Networking basics
#### Networks : 
- A computer networkis two or more client machines that are connected together to share resources. A network can be logically partitioned into subnets. 

- Networking requires a networking device (such as a router or switch) to connect all the clients together and enable communication between them.AWS Training and Certification Module 5: Networking and Content Delivery.

#### IP addresses : 
- Each client machine in a network has a unique Internet Protocol (IP) address that identifies it. An IP address is a numerical label in decimal format. 
- Machines convert that decimal number to a binary format.In this example, the IP address is 192.0.2.0.
- Each of the four dot (.)-separated numbers of the IP address represents 8 bits in octal number format. That means each of the four numbers can be anything from 0 to 255. The combined total of the four numbers for an IP address is 32 bits in binary format.

#### IPv4 and IPv6 addresses :
- An IPv6 address is made up of eight groups of four hexadecimal characters (a combination of numbers and letters), separated by colons (:).
- For example: 2600:1f18:22ba:8c00:ba86:a05e:a5ba:00FF. Each group represents 16 bits, with values ranging from 0000 to FFFF in hexadecimal format.
- When all eight groups are combined, they form a complete 128-bit address.
- This larger address space in IPv6 allows for a significantly greater number of unique IP addresses compared to IPv4, making it suitable for the growing number of internet-connected devices.

#### Classless Inter-Domain Routing (CIDR) : 

CIDR is a way to represent IP address ranges efficiently. It uses this format:
- IP_address/prefix_length
  - The IP address is the starting address of the network.
  -	The prefix length (after the slash /) tells how many bits are fixed as the network identifier.
  -	The remaining bits are variable, allowing multiple IP addresses in that range.
- Example:
  -	192.0.2.0/24: First 24 bits are fixed; last 8 bits vary. This gives 256 addresses (192.0.2.0 to 192.0.2.255).
  -	192.0.2.0/16: First 16 bits are fixed; last 16 bits vary. This gives 65,536 addresses (192.0.0.0 to 192.0.255.255).
- Special cases:
  -	192.0.2.0/32: All 32 bits are fixed; represents a single IP address (useful for firewalls).
  -	0.0.0.0/0: No bits are fixed; represents all IP addresses on the internet.

###  Open Systems Interconnection (OSI) model

The Open Systems Interconnection (OSI) model is a conceptual framework that explains how data moves across a network. It has seven layers, each responsible for specific network functions and protocols.
- Layer 2 (Data Link Layer): Devices like hubs and switches operate here.
- Layer 3 (Network Layer): Routers work at this layer, managing IP addressing and routing.
 
The OSI model helps in understanding communication in systems like Virtual Private Clouds (VPCs).

Additionally, ICA (Independent Computing Architecture) is a protocol developed by Citrix Systems to enable efficient data exchange between a server and client, often used in remote desktop and virtualization environments.


## Section 2: Amazon VPC	 

- Many of the concepts of an on-premises network apply to a cloud-based network, but much of the complexity of setting up a network has been abstracted without sacrificing control, security, and usability. 
- In this section, you learn about Amazon VPC and the fundamental components of a VPC


### Amazon VPC

Amazon Virtual Private Cloud (Amazon VPC) is a service that lets you create a logically isolated network within the AWS Cloud, where you can launch and manage AWS resources.

With Amazon VPC, you have full control over:
- IP address ranges (IPv4 and IPv6)
-	Subnets
-	Route tables
-	Network gateways

You can customize the network setup—for example:
- Create public subnets for web servers with internet access.
-	Place backend systems like databases in private subnets with no internet access.

To enhance security, VPC supports:
-	Security groups (virtual firewalls for EC2 instances)
-	Network access control lists (network ACLs) for controlling traffic at the subnet level.

### VPCs and subnets

Amazon VPC lets you create a logically isolated virtual network in the AWS Cloud, dedicated to your account. 

Each VPC is region-specific and can span multiple Availability Zones (AZs).

You can divide a VPC into subnets, each tied to a single AZ.
-	Public subnets have internet access.-
-	Private subnets do not, and are used for backend resources.
-	
Creating subnets across different AZs helps ensure high availability.

### IP addressing
- IP addresses allow resources in your VPC to communicate internally and with the internet.
- When you create a VPC, you assign an IPv4 CIDR block—a fixed range of private IPv4 addresses (from /16 with 65,536 addresses to /28 with 16 addresses).
- This range cannot be changed later, so choose carefully.
- You can also optionally add an IPv6 CIDR block for IPv6 addressing.
- Subnets within a VPC have CIDR blocks that are either the same size as the VPC or subsets of it.
- Multiple subnets can be created as long as their CIDR blocks do not overlap, preventing duplicate IPs in the VPC.

### Reserved IP addresses

When you create a subnet, it must have its own CIDR block. AWS reserves five IP addresses within each subnet’s CIDR block for specific purposes, so they aren’t available for use. 

These reserved addresses are for:
-	Network address
-	VPC local router (internal communication)
-	DNS resolution
-	Future use
-	Network broadcast address

For example, a subnet with a 10.0.0.0/24 CIDR block has 256 total IP addresses, but only 251 are usable because of these reservations.

### Public IP address types

- When you create a VPC, every instance automatically gets a private IP address.
- You can also enable auto-assign public IPs in the subnet settings to give instances public IP addresses when launched.
- An Elastic IP address is a static, public IPv4 address designed for cloud use. You can associate it with any instance or network interface in your VPC.
- Elastic IPs let you quickly remap addresses to another instance to handle failures.

Associating an Elastic IP with a network interface (instead of directly with an instance) allows you to move the interface—and all its settings—between instances easily.

### Elastic network interface

- An Elastic Network Interface (ENI) is a virtual network interface that you can attach or detach from an instance in a VPC. 
- When moved to another instance, the ENI retains all its attributes, and network traffic is redirected to the new instance.
- Each instance has a primary network interface with a private IPv4 address assigned from the VPC’s range, which cannot be detached.
- You can also create and attach additional ENIs to instances, with the number allowed depending on the instance type

### Route tables and routes

A route table contains rules called routes that direct network traffic from your subnet. Each route has:
-	a destination (a CIDR block where the traffic is headed), and
-	a target (where the traffic is sent through).

By default, every route table includes a local route for communication within the VPC, which cannot be deleted.

Every subnet must be associated with one route table. The main route table is assigned automatically to your VPC and controls subnets not explicitly associated with another table.

A subnet can be linked to only one route table, but a route table can be associated with multiple subnets.



### Section 2 key takeaways
- A VPC is a logically isolated section of the AWS Cloud.
- A VPC belongs to one Region and requires a CIDR block.
- A VPC is subdivided into subnets.
- A subnet belongs to one Availability Zone and requires a CIDR block.
- Route tables control traffic for a subnet.
- Route tables have a built-in local route.
- You add additional routes to the table.
- The local route cannot be deleted

## Section 3: VPC networking

### Internet gateway 

An internet gateway is a scalable and highly available VPC component that enables communication between your VPC instances and the internet. It serves two main functions:
-	Acts as a target in your route tables for internet-bound traffic.
-	Performs network address translation (NAT) for instances with public IPv4 addresses.

To make a subnet public, you attach an internet gateway to your VPC and add a route in the subnet’s route table directing all non-local traffic (0.0.0.0/0) through the internet gateway.

### Network address translation (NAT) gateway

A NAT gateway allows instances in a private subnet to access the internet or other AWS services while blocking inbound internet traffic from initiating connections to those instances.

To set up a NAT gateway:
-	Place it in a public subnet.
-	Associate it with an Elastic IP address.
-	Update the route table for private subnets to send internet-bound traffic to the NAT gateway.

This enables private instances to communicate with the internet securely.

While you can use a NAT instance instead, NAT gateways are managed services offering better availability, higher bandwidth, and less management, so AWS generally recommends using NAT gateways.

### VPC sharing

VPC sharing lets you share subnets with other AWS accounts within the same AWS Organization. 

This allows multiple accounts to create and manage resources—like EC2 instances, RDS databases, Redshift clusters, and Lambda functions—within shared, centrally managed VPCs.
-	The VPC owner shares subnets with participant accounts in the organization.
-	Participants can create, view, modify, and delete their own resources in shared subnets but cannot access others’ resources.

Benefits of VPC sharing include:
-	Separation of duties: Central control over VPC structure, routing, and IP allocation.
-	Ownership: Application owners keep control of their resources, accounts, and security groups.
-	Security groups: Participants can reference each other’s security groups.
-	Efficiency: Better subnet density and efficient use of VPNs and Direct Connect.
-	No hard limits: Simplifies architecture to avoid limits like 50 virtual interfaces per Direct Connect.
-	Cost optimization: Shares NAT gateways, interface endpoints, and reduces intra-AZ traffic costs.

VPC sharing simplifies network management by enabling fewer, larger, centrally managed VPCs, benefiting highly interconnected applications.

### VPC peering

A VPC peering connection is a private network link between two VPCs that allows instances in either VPC to communicate as if they were on the same network. 

You can peer VPCs within your account, across different AWS accounts, or even across different AWS Regions.

To enable communication, you add routes in each VPC’s route table pointing to the other VPC’s IP range via the peering connection.

Key restrictions:
-	IP address ranges cannot overlap.
-	Transitive peering is not supported (e.g., if VPC A peers with B and C, B and C cannot communicate unless explicitly peered).
-	Only one peering connection is allowed between the same two VPCs.

More details: AWS VPC Peering Documentation

### AWS Site-to-Site VPN

By default, instances in a VPC cannot communicate with remote networks. To connect your VPC to a remote network via a VPN:
- 1.	Create and attach a VPN gateway (virtual private network gateway) to your VPC.
- 2.	Define the customer gateway configuration—this AWS resource represents your VPN device’s info.
- 3.	Create or update a route table to send traffic destined for your corporate network to the VPN gateway. Also, update security group rules accordingly.
- 4.	Establish an AWS Site-to-Site VPN connection linking your VPC and remote network.
- 5.	Configure routing to pass traffic through the VPN connection.

For details, see AWS VPN Connections Documentation.

### AWS Direct Connect

- Network performance can suffer if your data center is far from your AWS Region.
- To address this, AWS offers AWS Direct Connect (DX), which lets you set up a dedicated, private network connection between your network and an AWS Direct Connect location.
- This private link can reduce costs, increase bandwidth, and provide a more consistent experience than internet connections. DX uses standard 802.1q VLANs for virtualization.

For more details, visit the AWS Direct Connect page.

### VPC endpoints

A VPC endpoint is a virtual device that lets your VPC privately connect to supported AWS services and endpoint services via AWS PrivateLink, without needing an internet gateway, NAT device, VPN, or Direct Connect. Instances in your VPC don’t need public IPs to communicate with these services, and traffic stays within the Amazon network.

There are two types of VPC endpoints:
-	Interface VPC endpoint (interface endpoint): Connects to services powered by AWS PrivateLink, including AWS services, other AWS customers' services, and AWS Partner Network (APN) services. You pay hourly and data processing fees for these endpoints.
- Gateway endpoint: Used for specific AWS services (like S3 and DynamoDB) and incurs no extra charges beyond standard data transfer fees.

For more info, check out the AWS VPC Endpoints documentation.

### AWS Transit Gateway
- We can configure your VPCs using various connectivity options like AWS Direct Connect, NAT gateways, internet gateways, and VPC peering.
- Many AWS customers have hundreds of VPCs across accounts and regions, making connectivity complex because all connections are point-to-point.
- Managing many VPC-to-VPC links can quickly become difficult and costly.
- While VPC peering works for connecting pairs of VPCs, it doesn’t scale well for large networks, especially when managing VPNs for each VPC individually.
- To simplify this, AWS Transit Gateway offers a hub-and-spoke model that acts as a central hub connecting all your VPCs, on-premises data centers, and remote offices.
- Instead of creating individual connections between every network, each network connects only to the transit gateway.
- This reduces management overhead, lowers costs, and makes it easier to scale as your network grows.

## Section 4: VPC security

We can secure your VPC by controlling both incoming and outgoing traffic using two key firewall options: security groups and network access control lists (network ACLs). 

These tools give you flexible control over traffic to help protect your resources within the VPC.

### Security groups (1 of 2) :
- A security group is like a virtual firewall for your instance that controls inbound and outbound traffic.
- It works at the instance level, not the subnet level, so different instances in the same subnet can have different security groups.
-  Essentially, security groups let you filter and control the traffic allowed to reach your instances.


### Security groups (2 of 2)
- Security groups have rules that control inbound and outbound traffic. When you create a security group, it starts with no inbound rules, so no inbound traffic is allowed until you add rules.
- By default, it allows all outbound traffic, but you can restrict that by adding outbound rules. If there are no outbound rules, no outbound traffic is allowed.
- Security groups are stateful, meaning if your instance sends a request, the response is automatically allowed back in, even if there’s no inbound rule for it. Similarly, responses to allowed inbound traffic are allowed out regardless of outbound rules.

### Network access control lists (network ACLs 1 of 2)
- A network access control list (network ACL) is an optional security layer that acts as a firewall for controlling traffic in and out of one or more subnets.
-  Each subnet must be associated with one network ACL. If you don’t specify one, the subnet uses the default network ACL.
-  A network ACL can be associated with multiple subnets, but each subnet can only have one network ACL at a time. When you associate a new ACL with a subnet, it replaces the previous one.

### Network access control lists (network ACLs 2 of 2)
- A network ACL has separate inbound and outbound rules that can allow or deny traffic.
- Your VPC includes a default network ACL that allows all inbound and outbound IPv4 (and IPv6 if applicable) traffic.
- Network ACLs are stateless, so they don’t keep track of traffic once a request is processed.

### Security groups versus network ACLs:

clear summary of the differences between security groups and network ACLs:
-	Scope: Security groups work at the instance level; network ACLs work at the subnet level.
-	Rules: Security groups only allow traffic (allow rules); network ACLs can allow or deny traffic.
-	Statefulness: Security groups are stateful (remember traffic state); network ACLs are stateless (do not track state).
-	Rule evaluation: Security groups evaluate all rules before allowing traffic; network ACLs evaluate rules in numerical order until a match is found.

### The key takeaways from this section of the module are:
- Build security into your VPC architecture.
- Security groups and network ACLs are firewall options that you can use to secure your VPC.


## Section 5: Amazon Route 53

### Amazon Route 53 : 
- Amazon Route 53 is a scalable and reliable DNS service that translates domain names into IP addresses.
-  It routes traffic to AWS resources or external endpoints, supports health checks to ensure availability, and offers various routing policies for global, fault-tolerant architectures.
-  It also provides domain registration and an easy-to-use traffic management interface.

### Amazon Route 53 DNS resolution

Amazon Route 53 routing policies:
-	Simple routing: Routes traffic to a single resource (e.g., one web server).
-	Weighted routing: Distributes traffic among multiple resources based on assigned weights, useful for A/B testing.
-	Latency routing: Directs traffic to the AWS region with the lowest latency for the user.
-	Geolocation routing: Routes traffic based on the user’s location, allowing localized content or geographic restrictions.
-	Geoproximity routing: Routes traffic based on resource locations and can shift traffic between them.
-	Failover routing: Enables active-passive failover by redirecting traffic if a primary site is down, using health checks.
-	Multivalue answer routing: Returns up to eight healthy records randomly for DNS queries, improving availability and basic load distribution (not a full load balancer).
  
### Use case: Multi-region deployment

Multi-Region Deployment Use Case:
Amazon Route 53 directs users automatically to the closest Elastic Load Balancing load balancer, improving performance.

Benefits:
-	Latency-based routing to the nearest AWS Region
-	Load balancing across Availability Zones within the Region

### DNS failover for a multi-tiered web application

### Route 53 for high availability with failover:
- 1.	Create two CNAME DNS records using Failover Routing:
  -	Primary record points to your web app’s load balancer.
  -	Secondary record points to a static Amazon S3 website as backup.
- 2.	Use Route 53 health checks to monitor the primary site.
  -	Traffic goes to the primary while it’s healthy.
  -	If the primary web server or database fails, traffic automatically fails over to the static backup site.

### Key takeaways from this section of the module include:
- Amazon Route 53 is a highly available and scalable cloud DNS web service that translates domain names into numeric IP addresses.
- Amazon Route 53 supports several types of routing policies.
- Multi-Region deployment improves your application’s performance for a global audience.
- You can use Amazon Route 53 failover to improve the availability of your applications.

## Section 6: Amazon CloudFront
- Networking enables sharing information between connected resources. You’ve learned about Amazon VPC for networking options to connect to the internet, remote networks, other VPCs, and AWS services.
-  Content delivery also happens over networks—for example, streaming movies. Now, you’ll learn about Amazon CloudFront, a content delivery network (CDN) service.

### Content delivery and network latency
- Network performance can be affected by the number of hops and distance between users and the origin server, causing latency and slower responsiveness.
- Because latency varies by location, using a content delivery network (CDN) like Amazon CloudFront can help improve performance by delivering content closer to users.

### Content delivery network (CDN)
- A content delivery network (CDN) is a global network of caching servers that store copies of static files (like HTML, CSS, JavaScript, and images) from the origin server.
- It delivers content from the closest edge location to the user for faster performance. CDNs also improve delivery of dynamic content by maintaining secure, low-latency connections near the user and efficiently routing requests back to the origin when needed.

### Amazon CloudFront:
- Amazon CloudFront is a fast, secure CDN that delivers data, videos, apps, and APIs globally with low latency and high speeds.
- It uses a network of edge locations and regional caches to optimize delivery. CloudFront offers high performance without costly contracts or minimum fees, and features pay-as-you-go pricing with a developer-friendly environment.

### Amazon CloudFront infrastructure
- Amazon CloudFront delivers content via a global network of edge locations, routing users to the nearest one for the lowest latency and best performance.
- Popular content is cached at these edge locations, while less popular content is stored longer at Regional edge caches, which sit between the origin server and edge locations.
- This setup reduces trips to the origin server and improves overall delivery speed for users.

### Amazon CloudFront benefits:
- Fast and global
- Security at the edge
- Highly programmable
- Deeply integrated with AWS
- Cost-effective

### Amazon CloudFront pricing
- Data transfer out :
  - Charged for the volume of data transferred out from Amazon CloudFront edge location to the internet or to your origin.
- HTTP(S) requests:	
  - Charged for number of HTTP(S) requests.
- Invalidation requests
  - No additional charge for the first 1,000 paths that are requested for invalidation each month. Thereafter, $0.005 per path that is requested for invalidation.
- Dedicated IP custom SSL :
  - $600 per month for each custom SSL certificate that is associated with one or more CloudFront distributions that use the Dedicated IP version of custom SSL certificate support.

## Lab 2: Build Your VPC and Launch a Web Server

In this lab, you use Amazon VPC to create your own VPC and add some components to produce a customized network. You create a security group for your VPC. You also create an EC2 instance and configure it to run a web server and to use the security group. You then launch the EC2 instance into the VPC.

- Created an Amazon VPC.
- Created additional subnets.
- Created an Amazon VPC security group. 
- Launched a web server instance on Amazon EC2.

