# AWS-Core-Services

<img src="https://github.com/user-attachments/assets/caafa064-00c0-4428-9ae7-c59e383638a4" width = "550" >

## 1. Amazon VPC (Virtual Private Cloud) 
- Launch AWS resources in a logically isolated virtual network. Multiple layers of security to control acceess to EC2 instances in each subnet.
- Create public facing subnet web servers that have access to the internet.
- Create private facing subnet for backend systems, such as databases and application servers.

VPC can increase and monitor the security of the VPC on demand, allowing creation nad termination of data centers when needed. VPC provides the following benefits:
- Advanced security features on inbound and outbound trafic at the instance and subnet level.
- Less set up, managment and validation needed.
- Control over Virtual networking environment. (IP address range, subnets, routing tables.)

<img src="https://github.com/user-attachments/assets/9ed49944-7c5f-4d8c-876f-e2e5313bf9ef" width = '550' />

*How to use Amazon VPC:*
- Host a simple website.
- Host Mult-tier web applications and enforce access and security restrictions between web servers, application servers and databases.
- Periodic back up of critical data from data center to EC2 instances for backup data recovery. Or import VM images to EC2 during disaster recovery period.
- Move corporate applications to cloud or lauch additional web servers. Or add compute capacity to network.

***When deleting a VPC, first terminate any EC2 or RDS instances provisioned in the VPC.***

VPC at basic level is free but additional features such as NAT gateway and elastic IPs have associated charges. 

## 2. Amazon EC2 (Elastic Compute Cloud)
- Web service that provides secure, resizable compute capacity in the cloud. Use web interface to obtain and configure capacity.
- Do not need to predict compute capacity for upfornt needs. Scalable to meet your needs.

EC2 has the following benefits:
- Set up an instance within minutes. Options for CPU, storage, and OS.
- Volume size and instance type can be changed without terminating the instance.
- Scale up or down to meet needs. Extra servers not needed can be removed to minimize cost.

<img src="https://github.com/user-attachments/assets/10d99cd6-e43b-4db0-afde-503f07a33925" width = "550" />

*How to use Amazon EC2*
- Host multi-tier applications with security groups. Control over port traffic to reach the instances.
- Create Backup instance that can be scaled up to the main instance capabilities until it is active. Can back up cloud or on-premises instances.
- Provision instances to perform computing jobs and terminate them when done. Cuts cost for short duration computing resources.
- Host databases (fully managed and serverless). But there is no access to the OS of the databases. Private owned database can be hosted if access is needed.

***Stoping an EC2 instance returns the volume to AWS. The Amazon Elastic Block Store (EBS) volume that is attached will retain your data. Charge for the volume will still be incurred, however all the data on the volume will be permanently deleted.***

EC2 has a few different pricing models:
- On-demand instances: Pay only for the amount of time that EC2 is used. No long term commitements or upfront payments. Changes to compute capacity depending on needs. **Used for short-term computing workloads that cannot be interrupted for low cost without commitment.**
- Spot instances: Discounted price for unused EC2 instances. Submit a request wiht the instance specifications and the maximum price you are willing to pay per hour. ***Used for workloads that can be paused and restarted when computing prices meet your budget.***
- Reserved instances: Discount upto 75%. Commit to paying for the instance for 1 or 3 years, depending on conditions during purchase. ***Used for computing needs with a steady amount usage of upto 1 year or more.***

## 3. Amazon RDS (Relational Database Service)
-  Simplifies setup,operations and scaling of relational databases.
-  Automated tasks such as patching, backing up and point-in-time recovery.
-  No need to anticipate database storage capacity for use over time. Flexible scalability.

<img src= "https://github.com/user-attachments/assets/0c9191b7-0056-4678-8503-17a4bc0ec7dd" width = "550" >

Amazon RDS has the following benefits:
- Easy to administer. No need for installation and maintenance.
- Fast and supports demanding database applications.
- Can be run in Amazon VPC or the instances can be connected to existing private IT infrastructure through IPsec VPN.

Architect can be build for fault tolerance by configuring Amazon RDS for Multi-AZ deployment. (Master and standby RDS instances in different Availability zones)

*How to use RDS*
- Web and mobile applications: Large scale applications requires databases with high throughput, large storage and high availability.
- Ecommerce applications: RDS offers small and large ecommerce businesses a flexible, secured, highly scalable, and low-cost database solution for online sales and retailing. Managed Database meets Payment Card Industry (PCI) compliance. 
- Mobile and online games: Provides and manages database infrastructre with high througput and availability that can rapidly grow to meet user demand. 

***RDS is fully managed, and access will be required to manage OS and update security patches. This can be done with an EC2 instance to host the database.***

RDS follows the pay-only-for-what-you use model and has no minimum fee. Provides a selection of instance types that are optimized to fit different relational database use cases. 

## 4. Amazon CloudWatch
- Monitoring and observation service for DevOPs engineers, developers, security engineers, and IT managers.
- Provides data and actionable insights to monitor applications, respond to system-wide performance changes and optimize resource utilization.
- Unified view of the operational health through logs, metrics and events.
- Used to detect anomalous behavior, set alarms, automate actions and torubleshoot issues. 

<img src = "https://github.com/user-attachments/assets/94b16590-9986-4bb6-9dfa-0e90d8ac5f4a" width = "550">

In the example above CloudWatch recieves data on teh EC2 instance, When the CPU goes over a threshold, CloudWatch triggers Amazon EC2 Autoscaling to provision an additonal instance to help with the workload to prevent overloading.

Amazon CloudWatch has the following benefits:
- Collect metrics and logs from all AWS resources and on-premises servers. Monitoring from one platform.
- Maintain visibility across services, applications, and infrastructure.(CPU util, memory)
- Set alarms and take automated actions.  
*How to use CloudWatch*
- Infrastructure monitoring and troubleshooting. Visualize application and infrastructure stack. Correlates metrics and logs to understand and resolve root cause.
- Poractive resource optimization: Watches metric values against user specified thresholds or specified by ML models to detech anomalous behavior. Capacity and resource planning is automated. 
- Application monitoring: Monitors on cloud or on premise applications and collects data at every layer of the performance stack. 
   
***Some services provide basic CloudWatch monitoring at no additional charge with the option to upgrade at a price.***

CloudWatch does not require an upfront commitment or minimum fee; pay for what you use at the end of the month. Charges for alarms, custom events, metrics collection and dashboards that have be set up by the user apply.

## 5. Amazon SNS (Simple Notification Service)
- Web service that makes it easy to set up operate and send notifications from the cloud.
- Provides developers with highly scalable, flexible and cost-effective capability to publish messages from an application and immediately deliver them to subscribers.

<img src = "https://github.com/user-attachments/assets/94a619e1-946e-4b1a-9e5c-14885be7a282" width = "500" >

The image shows and EC2 instance failure which notifies CloudWatch. CloudWatch then triggers an action to create a new EC2 instance. At the same time, CloudWatch triggers SNS to notify the appropriate subscribers for further investigation. 

Amazon SNS has the following benefits:
- Send messages or notifications directly to users across 200 countries. SMS text, mobile push or email (SMTP).
- Strategies for messge durability. If a subscribed endpoint isn't availble, Amazon SNS initiates a message delivery retry policy to resend the message.

*How to use SNS*

You can use SNS to create topics.(**Topic**: An access point identifying a specific subject or event type.) SNS topics are defined as standard topics or FIFO topics. 
- Standard: Can be used in many scenarios if the application can process messages that arrive more than once and out of order. (media encoding, fraud detections, tax calculations, search index, and critical alerting systems.)
- FIFO: Enhances messaging between applications when the order of operations and events is critical or when duplicated can't be tolerated. (Bank transaction logging, stock monitoring, flight tracking, inventory managment, and price update systems.)

***SNS cannot automate messages by itself. It must work with a service such as CloudWatch or Lambda that monitors your architecture operations. The service must also be able to trigger SNS to send notifications.***

SNS has no upfront fees, no commitments or long term contracts. Pay for what you use and whay type of topic.

## 6. IAM (Identity and Access Management)
- Centralized security managment system that is included in every AWS account to control identity access to AWS services.
- Identities in IAM are users, groups and roles.
- Principle of least privilege.
- Able to grant someone from different AWS account access to your account to perform specific tasks. 

<img src = "https://github.com/user-attachments/assets/aee445bd-7960-4286-978a-2a4f5217d9ab" width = "400">

**a. User**: Entity that is created in AWS. Represents the person or service who uses the IAM user to interact with AWS.

**b. Group**: Collection of IAM users. Specify permissions for a collection of users for easier managment.

**c. Role**: Identity with permission policies that are attacehd to it. An IAM user or service can assume these policies to temporarily take on different permissions for a specific task. 

Amazon IAM has the following benefits:
- Simple user interface.
- System-generated policies and option to create additional custom policies that meet specific requirements. 

*How to use IAM*
- Fine-grained access control: Control access to AWS service APIs and specific resources. Add specific conditions for how a user can use AWS resources or their originting IP address.
- Multi-factor authentication: MFA available at no extra cost. Users are required to prove physical possession of hardware MFA token or MFA enabled mobile device with a code.
- Analyze access: Helps analyze access across AWS environment. Security teams and administrators can validate policies. Identify and refine policies to adhere to the principle of least provolege.
  
***AWS evaluates policies depending on types of policies:***
***- Implicit deny: Denies a user, group or a role access. Default setting, requires explicit allow IAM policy attached to the identity.***
***- Explicit allow: Overrides implicity deny. Grants full or partial access.***
***- Explicit deny: Restricts the identity's access. Explicit allow cannot override explicit deny.***

No additional charge for IAM. Charges apply only when you access other AWS services by using IAM's user's credentials.

## 7. Amazon S3
- Object storage to store and retireve any amount of data from anywhere at any time. 
- Removes the issue of estimating the storage space needed. Simply create your bucket and add as many files as needed. Elastic and scales automatically.
- Files uploaded to S3 are automatically replicatd across AZs in the region.

In the example, S3 is being used to host a static website. The content is uploaded to S3 and directed to Amazon CloudFront to deliver the content to the internet.

<img src = "https://github.com/user-attachments/assets/0ef3502f-d19b-4272-82e5-0b0ad02ad64e" width = "400">

Amazon S3 has the following benefits:
- Offers durability, availabiltiy, performance, security, and scalability.
- Serverless, hence higly scalable.
- Security, compliance, and audit capabilities.

*How to use S3*
- Backup and restore: Build scalable, durable and secure backup and restore solutions. (Replaces on-premises capabilities)
- Disaster Recovery: Avoid expense of a second physical site by storing data, applicaitons, and systems in the cloud or in on-premises environment.
- Archive: Amazon Simple Storage Service Glacier and S3 Glacier Deep Archive retains objects long-term at low rates. Create an S3 Lifecycle policy to archive objects throughout their lifecyles or upload objects directly.
- Data Lakes and big data analytics: Extract insights by using query-in-place, analytics and machine learning tools. 

***S3 is desiged for Object storage (Read intesive files tath are not written to) and not block storage (More structured set of dat hosting that is written to) Examples: Pictures, videos, documents and static websites.***

Pay only for what you use, no minimum fee. May vary across regions. 

## 8. AWS Lambda
-

<>

Amazon Lambda has the following benefits:

*How to use Lambda:*

***Imp***
## 9. Amazon DynamoDB
