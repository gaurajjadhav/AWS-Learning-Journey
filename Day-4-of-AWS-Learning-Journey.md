# Day 4: AWS Cloud Security
## Topics: 
- AWS shared responsibility model
- AWS Identity and Access Management (IAM)
- Securing a new AWS account
- Securing accounts
- Securing data on AWS
- Working to ensure compliance
## Activities
- AWS shared responsibility model activity
## Demo
- Recorded demonstration of IAM
## Lab
- Introduction to AWS IAM
## Knowledge check Done!





# Section 1: AWS shared responsibility model
### AWS shared responsibility model 

      Security and compliance on AWS follow a shared responsibility model, designed to reduce the customer’s operational burden while offering flexibility and control. AWS is responsible for security of the cloud, which includes managing infrastructure, software, networking, and the physical security of its data centers. Customers are responsible for security in the cloud, such as encrypting data at rest and in transit, managing security credentials and logins, configuring security groups, and maintaining their operating systems — including updates and patches. This clear division ensures secure and efficient deployment of customer solutions on AWS.

AWS responsibility: Security of the cloud
     Under the AWS shared responsibility model, AWS manages and secures everything from the bare metal infrastructure and virtualization layer to the physical security of its global facilities. This includes AWS Regions, Availability Zones, and edge locations. AWS is responsible for:
-	Physical security: Restricted, need-based access to data centers, 24/7 guards, surveillance, two-factor authentication, and secure destruction of hardware.
-	Hardware infrastructure: Servers, storage devices, and essential appliances.
-	Software infrastructure: Operating systems, service applications, and virtualization tools.
-	Network infrastructure: Routers, switches, firewalls, and load balancers, with constant monitoring, secure access points, and intrusion detection.
AWS’s top priority is protecting this infrastructure. Although customers can’t access data centers, AWS provides third-party audit reports to verify compliance with major security standards.

### Customer responsibility: Security in the cloud

         In the AWS shared responsibility model, customers are responsible for what they implement using AWS services and how they secure their applications and data. Responsibilities include managing operating systems, application security, network and firewall configurations, security groups, and account access.
Customers retain full control over their content and must decide:
-	What data to store on AWS
-	Which services to use
-	Where (geographically) the data is stored
-	How the data is formatted, encrypted, or anonymized
-	Who can access the data and how access is managed
Ultimately, customers are responsible for protecting their data, applications, IAM settings, and overall cloud environment based on their specific use case and system complexity.

### Service characteristics and security responsibility

Infrastructure as a Service (IaaS) provides the fundamental building blocks of cloud IT, such as virtual machines, storage, and networking. These services offer the highest level of flexibility and control over IT resources, closely resembling traditional on-premises infrastructure. In AWS, services like Amazon EC2 fall under IaaS. Customers using IaaS are fully responsible for configuring and managing the guest operating system, applying updates and patches, securing applications, and setting up security groups and firewall rules.
Platform as a Service (PaaS) abstracts much of the underlying infrastructure, allowing customers to focus on building and deploying applications without worrying about hardware, operating systems, or patching. AWS services like AWS Lambda and Amazon RDS are examples of PaaS. AWS handles infrastructure operations including OS and database patching, capacity planning, and disaster recovery. Customers are responsible for managing the data they store, applying access controls, and ensuring proper classification and protection of their digital assets.
In short, IaaS gives full control and more responsibility to the customer, while PaaS simplifies operations by letting AWS handle most infrastructure and platform-level tasks.
Software as a Service (SaaS) delivers centrally hosted software accessible via web browsers, mobile apps, or APIs. SaaS typically follows a subscription or pay-as-you-go model. Customers using SaaS do not manage the underlying infrastructure, which simplifies deployment and maintenance.
In AWS, services like AWS Trusted Advisor, AWS Shield, and Amazon Chime are examples of SaaS:
-	AWS Trusted Advisor analyzes your AWS environment and offers real-time recommendations to optimize performance, security, and cost. Basic checks are free, while full access is included with Business or Enterprise Support plans.
-	AWS Shield is a managed DDoS protection service that automatically detects and mitigates threats. Shield Advanced offers enhanced protection and access to the DDoS Response Team, available with Business or Enterprise Support.
-	Amazon Chime is a pay-as-you-go communication service for meetings, chat, and calls, with no upfront fees or long-term contracts.
With SaaS, AWS handles all infrastructure and platform tasks, allowing customers to simply use the software as needed.


# Section 2: AWS Identity and Access Management (IAM)
### AWS Identity and Access Management (IAM)

             AWS Identity and Access Management (IAM) allows you to securely control access to AWS services and resources. It manages authentication (who can sign in) and authorization (what actions they can perform), offering fine-grained control over API calls across AWS.
With IAM, you can:
-	Define who can access specific resources
-	Control how they access them (read, write, admin, etc.)
-	Assign different permissions to different users or groups
-	Manage access using the AWS Console, CLI, or SDKs
For example, some users may have full access to EC2 and S3, while others may only view certain S3 buckets or manage specific EC2 instances. IAM can also restrict users to view only billing information.
IAM is a free service included with every AWS account and is essential for secure cloud resource management.

### IAM: Essential components

- An IAM user is an individual or application in an AWS account that makes API calls, each with a unique name and personal security credentials separate from the root account. Users belong to only one AWS account.
- An IAM group is a collection of users, helping simplify permission management by assigning policies to multiple users at once.
- An IAM policy is a document that defines permissions, specifying what actions users can perform on which resources. Policies can grant or explicitly deny access.
- An IAM role provides temporary access to AWS resources, allowing secure delegation of permissions without sharing long-term credentials


### Authenticate as an IAM user to gain access	

            Authentication means proving your identity before gaining access, similar to showing ID at airport security.
In AWS, when you create an IAM user, you assign one or both types of access:
- Programmatic access: The user gets an access key ID and secret access key to make API calls via AWS CLI, SDKs, or development tools.
   AWS Management Console access: The user logs in via a browser using the account ID or alias, IAM username, and password. If enabled, multi-factor authentication (MFA) adds an extra security code step.
### IAM MFA	

AWS servicesand resources can be accessed by using the AWS Management Console, the AWS CLI, or through SDKs and APIs. For increased security, werecommend enabling MFA. 
With MFA, users and systems must provide an MFA token—in addition to the regular sign-in credentials—before they can access AWS services and resources. 
Options for generating the MFA authentication token include virtual MFA-compliant applications(such as Google Authenticator or Authy 2-Factor Authentication), U2F security key devices, and hardware MFA devices

### Authorization: What actions are permitted

Authorizationis the process of determining what permissionsa user, service or application should be granted. After a userhas been authenticated, they must be authorizedto access AWS services. 
By default, IAM users do not have permissions to access any resources or data in an AWS account. Instead, you must explicitly grant permissions to a user, group, or roleby creating apolicy,which is a document in JavaScript Object Notation (JSON) format.A policy lists permissionsthat allowor deny access to resources in the AWS account

### IAM: Authorization

To assign permissions to a user, group, or role, you create or use an IAM policy. By default, all actions are denied (implicit deny) unless explicitly allowed, and any explicit deny always overrides allow.
The principle of least privilege means granting users only the minimum permissions they need. It’s best to start with limited access and add permissions as required, which enhances security.
IAM permissions and settings are global, applying across all AWS Regions, not limited to any specific region.

### IAM policies	

            An IAM policy is a formal set of permissions attached to IAM entities—users, groups, roles, or resources. Policies define which actions are allowed or denied, on which resources, and under what conditions. All policies are evaluated together, and the most restrictive rule always applies.
There are two main types of IAM policies:
-	Identity-based policies: Attached to users, groups, or roles to control their permissions. These include:
    -	Managed policies: Standalone policies reusable across multiple identities.
-	Inline policies: Embedded directly into a single user, group, or role.
    - Resource-based policies: Attached directly to resources (like S3 buckets), specifying who can access the resource and how

### IAM permissions

          IAM policies let you precisely control permissions for users, groups, and roles. When determining access, IAM first looks for any explicit deny. If none is found, it checks for an explicit allow. If neither exists, access is denied by default (implicit deny). A user can act only if the action is explicitly allowed and not explicitly denied.
To help test and troubleshoot permissions, AWS provides the IAM Policy Simulator tool:
https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html

### IAM groups

         An IAM group is a collection of IAM users that simplifies permission management. You attach policies to the group, and all users in that group inherit those permissions automatically. For example, a “Developers” group can have permissions common to developers; adding a user to the group grants them those permissions without assigning policies individually.
Key facts about IAM groups:
-	A group can have many users; a user can belong to multiple groups.
-	Groups cannot contain other groups (no nesting).
-	Groups only contain users.
-	There’s no default group with all users—you must create and manage such a group manually.


### IAM roles

        An IAM role is an AWS identity with specific permissions, similar to an IAM user, but meant to be assumed by anyone who needs it. Unlike users, roles don’t have long-term credentials like passwords or access keys; instead, they provide temporary security credentials when assumed.
Roles are used to delegate access to users, applications, or services that don’t normally have access, such as:
-	Granting temporary permissions to users within or across AWS accounts.
-	Allowing mobile apps to access AWS resources without embedding keys.
-	Providing access to external identities (e.g., corporate directories).
-	Enabling third parties to audit resources securely.
IAM roles are key for flexible, secure access in cloud deployments.


### Some keytakeaways from this section of the module include:

- IAM policies are constructed with JavaScript Object Notation (JSON) and define permissions.
- IAM policies can be attached to any IAM entity.
- Entities are IAM users, IAM groups, and IAM roles.
- An IAM user provides a way for a person, application, or service to authenticate to AWS.
- An IAM group is a simple way to attach the same policies to multiple users.
- An IAM role can have permissions policies attached to it,and can be used to delegate temporary access to users or applications
 
# Section 3: Securing a new AWS account

AWS account root user access versus IAM access
          When you create an AWS account, you start with a root user—an identity with full access to all resources, accessed via the email and password used to create the account. AWS strongly advises not to use the root user for daily tasks because it has unrestricted access.
Instead, create IAM users with specific permissions based on the principle of least privilege. For example, create an IAM user with admin access for full control, or users with read-only access as needed. Assign unique credentials to each user and avoid sharing credentials.
The root user should only be used for a few special tasks that require its full privileges. More details are available here:
https://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html#aws_tasks-that-require-root
	

### Securing a new AWS account: Account root user

- 1.	 While logged in as the root user, create an IAM user with AWS Console access (don’t attach permissions yet). Save access keys if needed.
- 2.	Create an IAM group (e.g., FullAccess), attach policies granting full access to needed services, and add your IAM user to this group.
- 3.	Disable and delete any root user access keys if they exist.
- 4.	Enable a password policy for all users, copy the IAM users’ sign-in link, and then sign out from the root user.
- 5.	Sign in using your new IAM user credentials via the sign-in link.
- 6.	Store root user credentials securely for emergencies.
For detailed guidance, see:
https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html

### Securing a new AWS account: MFA

       Require Multi-Factor Authentication (MFA) for the AWS account root user and all IAM users. MFA adds an extra layer of protection by requiring a time-based token along with the usual password or access keys.
You can also enforce MFA for programmatic access to APIs.
Options for generating MFA tokens include:
-	Virtual MFA apps like Google Authenticator or Authy
-	Physical U2F security key devices
-	Hardware MFA devices such as key fobs or display cards
For detailed instructions on setting up MFA for API access, check:
https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_configure-api-require.html

	

### Securing a new AWS account: AWS CloudTrail

AWS CloudTrail is a critical service for logging and auditing all API requests made to resources within your AWS account. It provides operational visibility by recording activities such as creation, modification, and deletion of supported AWS services.
By default, CloudTrail is enabled automatically when you create your AWS account, and it retains a record of the last 90 days of account management events. You can view and download this recent activity without needing to set up any additional configuration.
If you want to retain logs for longer than 90 days, or if you want to set up alerts for specific events (for example, suspicious activities or key configuration changes), you need to create a new CloudTrail trail. This trail can be configured to deliver logs to an Amazon S3 bucket and integrate with Amazon CloudWatch for monitoring and alerting.
For detailed guidance on how to create and configure a trail, you can follow the step-by-step instructions here:
https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-a-trail-using-the-console-first-time.html
To see which AWS services are supported by CloudTrail, visit:
https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html

### Securing a new AWS account: Billing reports

Another important step to secure and manage your new AWS account effectively is to enable billing reports, such as the AWS Cost and Usage Report. These reports give you detailed insights into your AWS resource usage and the estimated costs associated with that usage.
AWS generates these reports and delivers them to an Amazon S3 bucket that you specify. The reports are updated at least once daily, helping you track your AWS spending over time—whether by the hour or by the day.
Monitoring billing reports helps you identify unexpected usage patterns, control costs, and optimize your AWS environment.
For detailed instructions on how to create and configure an AWS Cost and Usage Report, you can visit:
https://docs.aws.amazon.com/cur/latest/userguide/cur-create.html

### The keytakeaways from this section of the module are all related to best practices for securing an AWS account. Those best practice recommendations include:

- Secure logins with multi-factor authentication (MFA).
- Delete account root user access keys.
- Create individual IAM users and grant permissions according to the principle of least privilege.
- Use groups to assign permissions to IAM users.
- Configure a strong password policy.
- Delegate using roles instead of sharing credentials.
- Monitor account activity using AWS CloudTrail.




# Section 4: Securing accounts
### AWS Organizations

AWS Organizations is a powerful account management service that lets you consolidate multiple AWS accounts into a single organization that you can centrally manage. From a security perspective, it offers several key features:
-	You can group accounts into Organizational Units (OUs) and apply different access policies to each OU. For example, if certain accounts need to comply with specific regulatory requirements, you can place them in one OU and attach policies that block access to AWS services that don’t meet those requirements.
-	AWS Organizations works seamlessly with IAM, extending control from individual users and roles within an account to the account level itself. Permissions that a user or role has are determined by the intersection of what the AWS Organizations policies allow and what IAM policies explicitly grant. This means a user can only access resources and perform actions allowed by both AWS Organizations and IAM policies.
-	It provides Service Control Policies (SCPs), which let you define the maximum permissions for all member accounts in your organization. SCPs restrict which AWS services, resources, and API actions can be accessed by users and roles in member accounts. These restrictions are enforced even if a member account administrator tries to grant broader permissions—SCPs always take precedence and block any disallowed access.
In summary, AWS Organizations enhances security by enabling centralized governance and strict permission boundaries across multiple AWS accounts, helping you enforce compliance and control access consistently across your organization

### AWS Organizations: Service control policies

-	SCPs provide centralized control over the maximum permissions that all accounts in your organization can have, ensuring accounts stay within your organization’s security and access guidelines.
-	SCPs require that your AWS Organization has all features enabled, including consolidated billing with full functionality. They are not available if your organization only uses consolidated billing features. You can enable SCPs by following the AWS guide on enabling/disabling policy types for your organization root.
-	SCPs look like IAM permission policies in syntax (JSON format), but unlike IAM policies, SCPs never grant permissions. Instead, they specify the upper limit of permissions that accounts or OUs in your organization can have.
-	Attaching an SCP to the root or an OU acts as a safeguard or guardrail restricting what actions member accounts can perform, but it does not replace IAM policies. You still must assign IAM policies to users and roles inside each account to grant actual permissions.
-	Think of SCPs as a permission boundary for accounts, limiting what can be done, while IAM policies are used inside accounts to grant permissions within those limits.
More details on enabling SCPs and managing policies are available in the AWS Organizations documentation, and IAM policies documentation explains how permissions are granted inside accounts.





### AWS Key Management Service (AWS KMS)

-	AWS KMS lets you create, manage, and control encryption keys used to protect your data across many AWS services and your own applications.
-	It uses hardware security modules (HSMs) validated under FIPS 140-2 standards, ensuring strong security and resilience for your encryption keys.
-	AWS KMS integrates with AWS CloudTrail to log all key usage events, which helps with auditing and meeting compliance requirements.
-	The core key in KMS is the Customer Master Key (CMK), which controls access to the data encryption keys that actually encrypt and decrypt your data.
-	You can create CMKs as needed, manage access permissions for them, and even import your own keys into AWS KMS if you have an existing key management infrastructure.
-	AWS KMS is integrated with most AWS services, so you can use CMKs to manage encryption for data stored in AWS services seamlessly.
For full details, you can visit the official AWS KMS features page:
https://aws.amazon.com/kms/features/

### Amazon Cognito

Amazon Cognito helps control access to AWS resources from your applications by defining roles and mapping users to those roles. This way, each user can access only the AWS resources they’re authorized for.
-	It supports industry identity standards like SAML 2.0, which enables integration with corporate identity providers (e.g., Microsoft Active Directory) for Single Sign-On (SSO). This means users can log in once with their corporate credentials and access multiple SAML-enabled apps without re-entering credentials.
-	Amazon Cognito is designed to meet security and compliance requirements for regulated industries, including:
   -	HIPAA compliance for healthcare workloads
   -	PCI DSS compliance for payment card data
   -	AICPA SOC (Service Organization Control) standards
   -	Various ISO/IEC standards such as ISO 27001, 27017, 27018, and ISO 9001
-	These compliance certifications help businesses in sensitive sectors trust Amazon Cognito to manage identity and access securely.
You can explore each compliance detail more here:
-	HIPAA: https://aws.amazon.com/compliance/hipaa-compliance/
-	PCI DSS: https://aws.amazon.com/compliance/pci-dss-level-1-faqs/
-	SOC: https://aws.amazon.com/compliance/soc-faqs/
-	ISO 27001/27017/27018:
    -	https://aws.amazon.com/compliance/iso-27001-faqs/
    -	https://aws.amazon.com/compliance/iso-27017-faqs/
    -	https://aws.amazon.com/compliance/iso-27018-faqs/
-	ISO 9001: https://aws.amazon.com/compliance/iso-9001-faqs

### AWS Shield

-	AWS Shield is a managed DDoS protection service that helps safeguard your AWS-hosted applications from Distributed Denial of Service attacks.
-	It offers always-on detection and automatic inline mitigation to minimize downtime and latency, without requiring manual intervention or contacting AWS Support.
-	It protects against various types of DDoS attacks:
    -	Infrastructure layer attacks (e.g., UDP floods)
    -	State exhaustion attacks (e.g., TCP SYN floods)
    -	Application layer attacks (e.g., HTTP GET or POST floods)
-	For practical examples, AWS WAF Developer Guide has more details: https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html
-Two tiers of AWS Shield:
  - AWS Shield Standard:
    -	Automatically enabled for all AWS customers
    -	No additional cost
    -	Provides baseline DDoS protection
-	AWS Shield Advanced:
    -	Paid, optional service
    -	Offers enhanced protection against larger and more sophisticated attacks
    -	Protects resources on EC2, ELB, CloudFront, Global Accelerator, and Route 53
    -	Access to the AWS DDoS Response Team (DRT) requires either Enterprise or Business Support plans.

# Section 5: Securing data on AWS
### Encryption of data at rest

-	Data encryption protects digital data by encoding it into an unreadable format unless decrypted with a secret key.
-	Data at rest means data physically stored on disks, tapes, or other storage devices.
-	On AWS, you can create encrypted file systems that encrypt all data and metadata at rest using the AES-256 encryption standard.
-	Using AWS Key Management Service (KMS), encryption and decryption happen automatically and transparently, so no application changes are needed.
-	If your organization requires data encryption for compliance or policy reasons, AWS recommends enabling encryption on all supported services that store your data.
-	AWS KMS supports many AWS services for encryption. More details can be found here:
https://docs.aws.amazon.com/kms/latest/developerguide/service-integration.html



### Encryption of data in transit

-	Data in transit means data moving across networks.
-	Encryption of data in transit uses Transport Layer Security (TLS) 1.2 with the AES-256 cipher. (TLS was formerly known as SSL.)
-	AWS Certificate Manager (ACM) helps you provision, manage, and deploy SSL/TLS certificates for AWS services and internal resources.
-	SSL/TLS certificates secure network communication and verify website/resource identities.
-	ACM can automatically handle certificate renewals.
-	Web traffic over HTTP is not secure, but traffic over HTTPS is encrypted with TLS/SSL, protecting against eavesdropping and man-in-the-middle attacks.
-	Many AWS services support encryption for data in transit.
-	Example: An EC2 instance using an Amazon EFS shared file system encrypts all data traffic between the instance and EFS using TLS/SSL.
For more details on EFS data in transit encryption, see:
https://docs.aws.amazon.com/whitepapers/latest/efs-encrypted-file-systems/encryption-of-data-in-transit.html

### Securing Amazon S3 buckets and objects

  By default, all S3 buckets are private. Only explicitly granted users can access them.
  Control tools for S3 access include:
-	Amazon S3 Block Public Access:
Overrides all other permissions to prevent public access. Enable this on buckets you want to keep private to avoid accidental exposure.
-	IAM Policies:
Define which IAM users or roles can access specific buckets or objects.
-	Bucket Policies:
Control access to buckets or objects, especially for cases where the user/system can’t authenticate via IAM.
    -	Can grant cross-account access or public/anonymous access (used carefully).
    -	Can include explicit deny statements to restrict access even if IAM permissions allow it.
-	Access Control Lists (ACLs):
An older way to control access, less commonly used now. Use cautiously to avoid overly permissive settings.
- AWS Trusted Advisor:
Has a bucket permission check tool to help identify buckets with overly broad or global access permissions.






# Section6: Working to ensure compliance

-	AWS partners with external certifying bodies and auditors to provide transparency about its policies, processes, and controls.
-	You can find a full listing of AWS Compliance Programs here:
AWS Compliance Programs.
-	To check which AWS services are covered by each compliance program, see:
AWS Services in Scope by Compliance Program.
Example: ISO/IEC 27001:2013 Certification
-	This standard requires a comprehensive Information Security Management System (ISMS).
-	AWS implements a rigorous security program aligning with ISMS principles to continuously manage security holistically.
other Key Regulations Supported by AWS
-	HIPAA — For healthcare-related data privacy and security.
-	GDPR — The European Union regulation protecting personal data and privacy, with extensive compliance resources available at:
AWS GDPR Center.
AWS’s built-in security features and legal frameworks help customers meet their compliance requirements under these and many other regulations.

### AWS Config

AWS Config is a powerful service for continuous monitoring and auditing of your AWS resource configurations. Here’s a quick summary:
-	What it does:
Continuously records and tracks configurations of your AWS resources.
- Key features:
    -	Automates evaluation of resource configurations against your desired rules or guidelines.
    -	Provides detailed history of resource configuration changes.
    -	Flags noncompliant resources, helping you quickly identify and fix issues.
    -	Simplifies compliance auditing, security analysis, change management, and troubleshooting.
-	Usage notes:
    -	AWS Config operates on a regional basis—enable it in every AWS Region you use to cover all resources.
    -	It offers an aggregator feature to consolidate views across multiple Regions and accounts for centralized compliance and inventory tracking
This makes AWS Config essential for maintaining governance and security posture across your AWS environment.


### AWS Artifact

-	On-demand access to audit reports like ISO certifications, PCI DSS, SOC reports, etc., which document AWS’s compliance posture.
-	Helps you share these official AWS documents with your auditors or regulators to demonstrate the security of the AWS cloud infrastructure you rely on.
-	Provides guidance documents to help you evaluate your own security controls and compliance practices in the cloud.
-	Allows you to review, accept, and track important legal agreements like the Business Associate Agreement (BAA) necessary for HIPAA compliance.
-	Supports centralized agreement acceptance across multiple AWS accounts via integration with AWS Organizations.
It’s important to remember that while AWS Artifact provides AWS-side compliance documentation, customers remain responsible for their own security controls and compliance evidence related to their data and workloads.
If you want to dig deeper, the AWS documentation on managing agreements in AWS Artifact is a great resource:
https://docs.aws.amazon.com/artifact/latest/ug/managing-agreements.html

### Some keytakeaways from this section of the module include:

- AWS security compliance programs provide information about the policies, processes, and controls that are established and operated by AWS.
- AWS Config is used to assess, audit, and evaluate the configurations of AWS resources.
- AWS Artifact provides access to security and compliance reports.

# Completed Lab : Introduction to AWS IAM

-	Explored pre-created IAM users and groups
-	Inspected IAM policies as applied to the pre-created groups
-	Followed a real-world scenario, adding users to groups with specific capabilities enabled
-	Located and used the IAM sign-in URL
-	Experimented with the effects of policies on service access

