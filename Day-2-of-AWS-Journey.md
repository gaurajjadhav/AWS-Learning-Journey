# Day 2 – AWS Academy Cloud Foundations  

## Cloud Economics and Billing

Topics Covered -
• Fundamentals of pricing
• Total Cost of Ownership
• AWS Organizations
• AWS Billing and Cost Management
• Technical Support

## Section 1: Fundamentals of Pricing
   1) AWS pricing model
   Three fundamental drivers of cost with AWS
      - a) Compute
          - Charged per hour/second
          - Varies by instance type
            *Linux only
      - b) Storage
         - Charge typically per GB
      - c) Data transfer
         - Outbound is aggregated and charged
         - Inbound has no charge  (with some exceptions)
         - Charged typically per GB

   2) How do you pay for AWS?
   AWS offers a range of cloud computing services. For each service, you pay for exactly the amount 
   of resources that you actually need. This utility style pricing model includes:
         - Pay for what you use
         - Pay less when you reserve
         - Pay less when you use more
         - Pay even less as AWS grows

   3) Pay for what you use
      
   Pay only for the services that you consume, with no large upfront expenses

   4)AWS Free Tier
   
   Enables you to gain free hands on experience with the AWS  platform, products, and services. Free for 1 year for new customers.

   5) Services with no charge
       - Amazon VPC lets you create a logically isolated virtual network in the AWS Cloud to launch your resources.
       - AWS IAM manages user access to AWS services and resources securely.
       - Consolidated Billing (via AWS Organizations) combines bills for multiple accounts, helps track charges, and can reduce costs through volume discounts.
       - AWS Elastic Beanstalk simplifies application deployment and management in the cloud.
       - AWS CloudFormation allows structured and predictable provisioning of AWS resources.
       - Automatic Scaling adjusts resources based on demand to maintain performance and reduce costs.
       - AWS OpsWorks helps deploy and manage applications of any size easily.

Section 2: Total Cost of Ownership
          1)	What is Total Cost of Ownership (TCO)?                                                   
                Total Cost of Ownership (TCO) is the financial estimate to help identify direct and indirect costs of a system.

          2)	Why use TCO?
                           • To compare the costs of running an entire infrastructure environment or specific workloadon-premises versus on AWS
                           • To budget and build the business case for moving to the cloud

          3)	AWS Pricing Calculator : Use the AWS Pricing Calculator to:
                           • Estimate monthly costs
                           • Identify opportunities to reduce monthly costs•Model your solutions before building them
                           • Explore price points and calculations behind your estimate
                           • Find the available instance types and contract terms that meet your needs
                           • Name your estimate and create and name groupsof services
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Section 3: AWS Organizations:
         1) AWS Organizations is a free account management service that lets you consolidate and centrally manage multiple AWS accounts. 

         2) It helps meet budget, security, and compliance needs with features like consolidated billing and account management.

         3) Benefits:
                          •	Centrally managed access policies
                          •	Controlled access to AWS services
                          •	Automated account creation and management
                          •	Consolidated billing across accounts

         4) Security with AWS Organizations:
                          •	 AWS Organizations does not replace IAM policies for managing users, groups, and roles within a single account.
                          • IAM policies control access to services, resources, or actions and apply only to IAM users, groups, or roles—not the root user.
                          •	Service Control Policies (SCPs) in Organizations manage access across accounts and apply to all identities, including the root user.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Section 4: AWS Billing and Cost Management:
         AWS Billing and Cost Management is the service that you use to pay your AWS bill, monitor your usage, and budget your costs. 
         Billing and Cost Management enables you to forecast and obtain a better idea of what your costs and usage might be in the future so that you can plan ahead.
         From the billing dashboard, you can access several other cost management tools that you can use to estimate and plan your AWS costs.
         These tools include AWS Bills, AWS Cost Explorer, AWS Budgets, and AWS Cost and Usage Reports.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Section 5: Technical support:
      1) AWS support Provide unique combination of tools and expertise:
                          • AWS Support 
                          • AWS Support Plans	

      2) Support is provided for:
                          • Experimenting with AWS
                          • Production use of AWS
                          • Business-critical use of AWS




