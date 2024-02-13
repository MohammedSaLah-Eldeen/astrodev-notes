### `Module @1`

### INTRODUCTION.

`1.1`

> All modern cloud computing uses the basic
> 
> **client-server model**.

- **`client-server model`.**
  
  : is a model where a computer - client - that needs something that it doesn't have, go and make a request to another computer - server - which have that thing.
  
     - the server is publicly available to the whole world and has a known address - domain name - for all other computers to request from it.

`1.2`

> key principle.
> 
> **Pay-as-you-go**

- you only pay on what you use. resources that aren't being used you don't pay for them at all.

`1.3`

> Is the on-demand delivery of IT resources over the internet with pay-as-you-go pricing.

- **On-demand delivery**
  
  the resources you need immediately when you need them you don't to tell anyone in advance!

- **IT resources**
  
  the common IT services across all businesses giving immediate access to setting up the `undifferentiated heavy lifting of IT` which are tasks that're common, repititive and time consuming

`1.4`

> Why Cloud Computing?

- Trade upfront expenses with variable expenses.

- Stop spending money on manging data centers.

- Stop guessing capacity.

- Benefit from massive economies of scale.

- Increase speed and agility.

- Go global in minutes.

### `Module @2`

### COMPUTE IN THE CLOUD.

`2.1`

> **AWS EC2**
> 
> (Elastic Compute Cloud)
> 
> Virtual Machines (VMs) that are configured and easily accessed. basically they're just servers.

> **AMI**
> 
> (Amazon Machine Image)
> 
> a template of software configuration such as OS, applications and application servers. it contains all the required info to launch an EC2 Instance.

- [Amazon Machine Images (AMI) - Amazon Elastic Compute Cloud](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)
  
     - READ the sub-articles of this article, find them in the left menu, for instance. (AMI types)

- it can be used to launch a single instance or a mulitple of them.

- *User data* 
  
  attribute in launching EC2 Instances.
  
  when launching an EC2 instance in advanced options you can provide provisioning scripts written in bash.

`2.1.1`

> EC2 **instance types**
> 
> VMs that're suited for certain tasks.

- [Compute – Amazon EC2 Instance Types – AWS](https://aws.amazon.com/ec2/instance-types/)

- [AWS Deep Learning: Choosing the Best Option for You](https://www.run.ai/guides/cloud-deep-learning/aws-deep-learning#:~:text=to%2080K%20IOPS-,Amazon%20EC2%20G4,to%204%20NVIDIA%20T4%20GPUs)

`2.1.2`

> EC2 Pricing models.
> 
> pay for what you need exactly

- `On-Demand`
  
  you pay for what you use, no more no less, it's best for irregular workflows for short periods, no commitments, once you want to opt out you opt out.

- `Savings Plan`
  
  you commit to spend some amount of money usually per hour 10$/hr for a one-year or 3 years. you get an average of 72% discount on all EC2 instances, meaning you can afford much more instances for the same amount X money more than on-demand. any spending that exceeds your commited price will be priced as on-demand.

- `Reserved Instances`
  
  you commit to reserve a specified number of EC2 instances of a specified type and family, you can only specify the region and the availability zone.

- `spot instances`
  
  unused compute power that's unused in AWS and they offer up to 90% discount over the on-demand prices. they're suited best for workflows that tolerate stopping and resuming as if AWS wants to reclaim the instance at any time it will do it.
  
  <img src="file:///C:/Users/msal7/AppData/Roaming/marktext/images/2024-01-29-23-02-49-image.png" title="" alt="" data-align="center">

`2.2`

> **Scalability**
> 
> The process of using the resources you need and only you need always, asking for more when you need more and asking for less when you need less.

- **EC2 AutoScaling**
  
  automatically request EC2 instances or delete based on the application demand
  
     - *Dynamic Scaling*
       
       responds to changing demands.
  
     - *Predictive Scaling*
       
       automatically schedule the right number of instances based on the predicted demand.
  
  Best Scaling is achieved with Dynamic and Predictive.

`2.2.1`

> **Scaling Types**

- **Scaling up** (vertically)
  
  Adding more power to an EC2 instance, t3.micro -> t3.large.

- **Scaling out** (horizontally)
  
  Adding more EC2 instances of the same power same to the one already running.

Scaling out > Scaling up, as you could have the increase of computing power you want while at the same time having another server to serve request and not busy the line.

`2.2.2`

> **AutoScaling Group**
> 
> the way to set up EC2 Auto scaling
> 
> which is a platform for horizontal scaling.
> 
> you need to set 3 numbers.

- min instances.

- desired instances.

- max instances.

`2.3`

> **ELB**
> 
> (Elastic Load Balancing)
> 
> even though EC2 AutoScaling can scale based on the demand it gets, they still need a load balancer to distribute the load between all the newly created instances.

- highly available load balancer that distribute load between servers efficiently and cost-effectively it can detect new ready spawnned instances and route traffic to them and also keep shut down instances up until they finish up and then forget about them all without any effort.

- ELB is a differnet service of EC2, but it works seamlessly with AutoScaling Groups.

- it can be used to route from users to the frontend and also route traffic from the frontend to the backend

`2.4`

> **Monolithic Applications**
> 
> (tightly coupled systems)

application that consists of tightly coupled components, therefore if anyone component fails it will make all the others fail as well.

`2.5`

> Microservices Applications
> 
> (loosely coupled systems)

applications that consists of loosely coupled systems micro applications, therefore if a micro application fails it won't affect the others.

`2.5.1`

> creating loosely coupled systems.

Services that can easily loosen a tight system are:

- SQS

- SNS

`2.5.1.1`

> **SQS**
> 
> (Simple Queue Service)
> 
> a message queueing service.

- send, store, retrieve messages between software components effectively loosening the direct link between them.
  
  frontend -> SQS <-> backend

- the frontend will never fail as it's able to route the requests always to SQS and will store them until the backend is awake again to receive requests.

`2.5.1.2`

> **SNS**
> 
> (Simple Notification Serivce)
> 
> a publish/subscribe service.

- You create a topic and let subscribers follow that topic and any message you send to a certain topic all of its subscribers will receive it.

- subscribers could be webservers, email addresses, AWS Lambda, etc..

`2.6`

> **Serverless**
> 
> You cannot see or access the underlying infrastructure, OS, etc..

- You won't need to provision or manage nor maintain any servers at all, *You just focus on your application code.*

`2.6.1`

> **AWS Lambda**
> 
> Lambda functions are functions that trigger some code whenever a trigger happen. 

- You just focus on the functionality of the code you never care about.
  
     - Provisioning
  
     - Scaling
  
     - Availability
  
     - Load Balancing
  
     - Maintaining

- it's because you don't have access to the underlying infrastructure and everything will be managet by AWS.

- **It's worth noting that a lambda function will timeout in a set time usually 15mins**

`2.7`

> **Containerization** (DOCKER)
> 
> have a control over your underlying infrastructure efficiently, with less headaches of VMs.

`2.7.1`

> **ECS**
> 
> (Elastic Container Service)

`2.7.2`

> **EKS**
> 
> (Elastic Kubernetes Service)

- both of these are container orchestration tools. 
  
  the tooling is just different.

- They run on EC2. that would also mean you need to manage your EC2,

- if you don't want to think about the OS at all use

`2.8`

> **Fargate**
> 
> a serverless compute platform for *ECS* or *EKS*

- you can use it to never think about any EC2 management.

### `Module @3`

### GLOBAL INFRASTRUCTURE AND RELIABLEITY.

`3.1`

> **AWS Regions**
> 
> AWS built its data centers around the globe.
> 
> Region is a geographical location where AWS has based some of its infrastructure.

- each region is identified by:
  
     - Continent/Region, (e.g. North America)
  
     - Location, Virginia
  
     - Code: us-east-1

`3.1.1`

> **Choosing a Region**

- ***Compliance*** with data governance and legal requirements.
  
  if your company conducting a business in a country that require you to hold your data in its boundries.

- ***Proximity***
  
  the more your applications are near to the customer the lower the latency is

- ***Service Availability***
  
  not all regions have all services.

- ***Pricing***
  
  even if two regions offer the same exact service with the same infrastructure, the price of a service differs from a region to another.

`3.2`

> **AZ**
> 
> (Availablity Zones)
> 
> each AWS Region has at least 2 AZs, most have 3 up to 6. An AZ contains 1 or more data centers typically 3.

- AZs are connected with each other with low latency, redundency and high availability. they're distant enough to prevent disastars from happening from one region to another.
- each AZ is named after its Region Code followed by a letter  (e.g. us-east-1a)

`3.3`

> **AWS Edge Locations**
> 
> if your application is hosted in one region and you have clients all over the globe instead of moving to all the other regions. *Edge Locations* use AWS CloudFront to store cached copies of your content closer to your customers for faster delivery.

- Edge Locations are separate from regions

`3.3.1`

> **AWS CloudFront**
> 
> is AWS CDN (content delivery network) which is the process of caching content nearer to customers all over the world.

`3.4`

> **Provision AWS Resources**
> 
> you can create and select your resources via

- AWS Managment Console.
  
  it becomes much more tedious to click through a lot pages to get a resource up and running.

- AWS CLI
  
  a more programmatic approach to set up services.

- AWS SDKs
  
  available in various langauages as well.

`3.4.1`

> **AWS Elastic Beanstalk**
> 
> you provide your application code and configuration settings, Elastic Beanstalk deploys the necessary resouces to perform the following tasks.

- Adjust Capacity.

- Load Balancing.

- Automatic Scaling.

- Application Health Monitoring.

`3.4.2`

> **AWS Cloud Formation**
> 
> an *IaC* (infrastructure as code) tool to provision and ready your cloud resources in lines of code (e.g. json, yaml) in the most safe and replicable manner.

`Module @4`

### NETWORKING.

`4.1`

> **VPC**
> 
> (Virtual Private Cloud)
> 
> Enables launching AWS resources in a logically defined isolated virtual network.

- A private network in AWS
  
  allows you to define your private IP range for the AWS resources
  
     - IP Range must be specified using
       
       **CIDR** Block
       
       allowed CIDR Block sizes are:
       
          - /16
       
          - /28
       
          - [What is CIDR? - CIDR Blocks and Notation Explained - AWS](https://aws.amazon.com/what-is/cidr/#:~:text=A%20CIDR%20block%20is%20a,regional%20internet%20registries%20(RIR).)

- resources are grouped in subnets.

- *subnets*
  
  chunks of IP addresses in VPC to allow of resource grouping.

- A subnet must live entirely in an AZ.

- **All AWS accounts come with a pre-configured VPC in each region**, that's you can launch resource instances right away without setting up your own.

- VPCs can span multiple AZs, **By Default a VPC spans all availability zones in a region.**

- You can create up to 5 VPCs in a region.

- You can have a maximum of 2500 security group per region.

`4.1.1`

> **IGW**
> 
> (Internet Gateway)
> 
> A way to allow public traffic from the internet to access your VPC

`4.1.2`

> **Virtual Private Gateway**
> 
> to allow traffic to your VPC using VPN only from trusted and authorized networks.

`4.1.3`

> **Subnets**

- In your VPC you can create 2 types of resources groups
  
     - Public subnet
       
       these are the resources that have access to the IGW.
       
       (e.g. webservers)
  
     - Private subnet
       
       resources that don't have access to the IGW.
       
       (e.g. database server)
       
       They could have access to the internet indirectly through NAT gateways (IPv4) or egress-only internet gateway (IPv6). 
  
  **NACLs** (Network access control lists)
  
  stateless firewall on all the resources of a subnet
  
  *by default, it allows all inbound and outbound traffic*
  
  **Security Groups**
  
  stateful firewall on each instance of any resource.
  
  *by default, it doesn't allow any inbound but all allows outbound traffic.*

`4.1.4`

> **Peering**

- [Connect VPCs using VPC peering - Amazon Virtual Private Cloud](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-peering.html)

- [What is VPC peering? - Amazon Virtual Private Cloud](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html)

`Module @5`

### STORAGE AND DATABASES.

`5.1`

> **EBS**
> 
> (Elastic Block Store)
> 
> Block-level Storage - Hard drives - to persist data.
> 
> storage that breaks files into smaller parts called blocks with each block having the same size.
> 
> suppose: File A; Blocks 1-5
> 
> modification to end of the file will only change the data in the fifth block.

- EC2 launched instances comes with a temporary block-level storage *Instance Store*. it's a physical Harddrive that's connected to the Host.
  
     - *Temporary*
       
       as VMs aren't strictly coupled with a particular Host EC2 stopped instances can start with a complete different Host, and since Instance Stores are storage that're provided from the Host, access to that storage is temporary and strictly coupled to the host itself.

- EBS to the rescue!
  
  Block-level - harddrives - storage that're 100% dedicated to storage workflow and persisting data. they're not strictly coupled with any instance. to create a volume you need to configure it with your needed size and type.
  
     - <span style="color: #4287f5">NOTE:</span> EBS volumes can't be accessed by multiple EC2 instances at the same time. but not vice verca, as an EC2 instance can access multiple EBS blocks. 

- EBS Snapshots:
  
  are incremental backups - Kind of version control - first backup to capture all data, next backups to capture changes to the files without recopying all the files all over again. you can also revert and rollback. 
  
     - Snapshots are usually persisted in S3 Storage.

`5.2`

> **S3**
> 
> (Simple Storage Service)
> 
> Object-level Storage to persist any data.
> 
> - storage that treats any file as a complete discrete object. modification to an object will result in a complete new object.
> 
> - Object Storage Service, an object consists of data and metadata and is defines by a key.
> 
> - Buckets are the containers that objects are stored in S3.

- All objects are addressable using a URL
  
  `http://<bucket-name>.s3.<region>.amazonaws.com/<object-path>`

- 11 9's (300 microseconds downtime in a year), automatically creates and stores copies across AZs.

- You can block public and users access to a bucket.

- You can upload up to 5GB in size with a single PUT operation for largers objects up to 5TB use multipart upload API.

- Object-level storage that's able to store everything and anything you throw at it. it doesn't have an installed FileSystem. *rathers paths and file system behaviours are just changes to the name with prefixes to imitate a FileSystem*. it stores everything in a flat address space with unique keys.

`5.2.1`

> **S3 Classes**

- S3 Standard.
  
  best for a range of use cases, web hosting and content distribution and data analytics. *Highest class cost*
  
     - Access Frequency: general purpose storage with **frequent access**
  
     - Time to access: **msec access**

- S3 Intelligent Tiering.
  
  requires a small monthly monitoring and automation fee per object.
  
     - Access Frequency: general purpose with **unknown or changing access patterns**. it moves data between IA and FA based on access patterns.
  
     - Time to access: **msec access**

- S3 IA (infrequent-access).
  
  best to store backups and disaster recovery files. it stores in a minimum of 3 AZs
  
     - Access Frequency: **infrequent access**
  
     - Time to access: **msec access**

- S3 One Zone - IA.
  
  best to store backups and disaster recovery files. it's cheapter than S3 IA but it doesn't have the same level of durability.
  
     - Access Frequency: **infrequent access** only store in one AZ, best suited for data that can be recreated.
  
     - Time to access: **msec access**

- S3 Glacier Instant Retrieval.
  
     - Access Frequency: long-term data achive digital preservation.
  
     - Time to access: **msec access**

- S3 Glacier Flexible Retrieval.
  
     - Access Frequency: long-term data achive digital preservation.
  
     - Time to access: **mins** or **Free bulk retrievals** 5-12hrs

- S3 Glacier Deep Archive.
  
     - Access Frequency: long-term data achive digital preservation. cheapest.
  
     - Time to access: **12-48hrs.

`5.2.2`

> **S3 Storage Class Analysis**
> 
> discover objects that should move to a lower cost storage class based on access patterns.

`5.2.2.1`

> *S3 LifeCycle Policy*
> 
> information from *1.2* can be used to configura this policy which makes the data transfer and defines when objects transition to a another storage class and when objects expire.

`5.2.3`

> **S3 CRR**
> 
> (Cross-Region Replication)
> 
> replicate data into other AWS regions.

`5.2.4`

> **S3 Object Lock**
> 
> objects are locked for the duration period define and prevented from deletion.

- A lot of policies can be enforced with S3 object lock such as, write-once, read-many, etc..

`5.2.5`

> **S3 Inventory**
> 
> view all list of objects and their encryption status.

`5.2.6`

> **S3 batch operations**
> 
> change object properties and perform storage management tasks for billions of objects.

`5.2.7`

> **S3 Lambda Integration**
> 
> you can log activites, define alerts and automate workflows.

`5.2.8`

> **S3 Query-in-place services for analytics**
> 
> supports analytics and big-data analytics in place with no need to copying to other analytics platform.

`5.2.9`

> **S3 Athena**
> 
> can query data stored in S3 with standard SQL experessions.

`5.2.10`

> **S3 Redshift**
> 
> can also run SQL queries at rest on S3. However, it's more appropriate to complex queries and large datasets up to exabytes!

`5.2.11`

> **S3 Select**
> 
> retrieves subsets of object data instead of the entire object, which can be up to terabytes.

- it's designed to increase query performance by up to 400% and reduce costs as much as to 80%.

`5.2.12`

> **S3 Versioning**
> 
> once versioning is enabled an object is thus identified by key + version.

- Bucket status.
  
     - Unversioned. (default)
  
     - Versioing enabled.
  
     - Versioning suspended. no new versions will be recorded but older versions are still available.

`5.2.13`

> **S3 Access Managment**
> 
> by default, buckets and objects are private. only the resource owner an AWS account that created it or the root, can access the resource.

- The resource owner can grant access to other users, serivces and applications by writing an Access Policy.

`5.2.14`

> **Access Policies**

- *Resource-based policies*
  
  attached to buckets and objects, such as.
  
     - Bucket policies. - recommended.
       
       are created for each bucket, it provides access permissions to the S3 bucket and all objects in it. uses json syntax.
       
       ![](file:///C:/Users/msal7/AppData/Roaming/marktext/images/2024-01-29-00-03-13-image.png?msec=1706991722190)
  
     - ACL. (Access Control List) - legacy.
       
       are created for each object and bucket. uses AWS XML-schema syntax.
  
  Query-string authentication to grant temporary access to others.

- *User Policies*
  
  attached to users using AWS IAM policies.

`5.1,2`

> **AWS EBS** VS. **AWS S3**
> 
> If files undergo a lot of changes EBS is the go, using complete objects with occasional changes S3 is the go.

- EBS sizes up to 16 TiB. and SSD by default with HDD options
  
     - Backups needed. 
  
     - web unenabled by default.

- S3 is Unlimited Storage, individual objects - files - up to 5 TBs, specialized in write once/read many.
  
     - No need for backups S3 is itself your backup plan.
  
     - web enabled by default.
  
     - cost savings compared to same storage load of EBS.
  
     - Serverless (no need to EC2 to access your storage.)

`5.3`

> **EFS**
> 
> (Elastic File System)
> 
> Managed File system. can be used in collabrative use cases where multiple users (e.g. people, applications, servers, etc..) need to access some data at the same time.

- [What is Amazon Elastic File System? - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)

- [Amazon EFS file system types and storage classes - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/availability-durability.html#file-system-type)

- [Amazon EFS performance - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/performance.html)

- [Amazon EFS: How it works - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/how-it-works.html#how-it-works-storage-classes)

- [Transferring data into and out of Amazon EFS - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/transfer-data-to-efs.html)

- [Using AWS DataSync to transfer data in Amazon EFS - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/trnsfr-data-using-datasync.html)

- [Using AWS Transfer Family to access files in your Amazon EFS file system - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/using-aws-transfer-integration.html)

- [Backing up your Amazon EFS file systems - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/awsbackup.html)

- [Amazon EFS Backup and Restore using AWS Backup | Amazon Web Services](https://aws.amazon.com/getting-started/hands-on/amazon-efs-backup-and-restore-using-aws-backup/)

`5.1,3`

> **AWS EBS** Vs. **AWS EFS**

- **EBS**
  
     - AZ level resource, EC2 instances need to be in same AZ as the EBS volume to access it.
  
     - Volumes don't automatically scale. (2 TB harddrive is a 2 TB harddrive)
  
     - you can do whatever with your harddrive, run databases, install applications everything you could do with a harddrive.

- **EFS**
  
     - Multiple instances can be reading and writing to the file system simultaneously.
  
     - A true Linux file system.
  
     - Region level resource.
  
     - Automatic Scaling up or down.

`5.4`

> **RDS**
> 
> (Relational Database Service)
> 
> A serverless relational database service.

- A service to let you focus on getting to write your first SQL query ASAP. getting the DB server to connect to your ORM ASAP. let's you think only in building your tables and schemas!
  
  no need to worry about
  
     - hardware provisioning.
  
     - database installation and setup.
  
     - patching.
  
     - creating backups.
  
     - setting up replicas! 
  
     - security (e.g. ecryption at rest and encryption in transit.)
  
  All is already done! with the power of scaling up or down as needed!

- Available Engines.
  
     - Amazon Aurora.
  
     - PostgreSQL
  
     - MySQL
  
     - MariaDB
  
     - Oracle Databases.
  
     - Microsoft SQL Server.

`5.4.1`

> **AWS Aurora**
> 
> is an enterprise-class DB engine, compatible with MySQL and PostgreSQL (you can migrate from these two seamlessly). it's up to five times faster than MySQL and 3 times faster than PostgreSQL.

- 1/10th the cost of commercial databases.

- creates 6 read replicas by default and supports up to 15 replicas at the same time.

`5.4.2`

> **Availability and Durability**

- **Automated Backups**
  
     - enabled by default.
  
     - it backs your database and transaction logs in S3 for a user-specified retention period up tp 35 days.
  
     - Allows point in time recovery.

- **Databases Snapshots**
  
     - user-created FULL backups stored in S3 and never deleted until the user deletes them.

- **Multi AZ Deployment**
  
     - Deploy your databases across multiple AZs in a region.

`5.4.3`

> **RDS Instance Classes**

- **Standard** (e.g. m1-m6)
  
  General purpose instances.

- **Memory Optimized Instances** (e.g. r5, r6g, z1d, x1)
  
  For memory intensive applications.

- **Burstable instances** (e.g. t2, t3)
  
  The ability to burst to its 100% CPU usage.

`5.4.4`

> **RDS Storage Type**

- **General Purpose**
  
  SSD Storage (gp2) provides a consistent baseline of 
  
  3 IOPS/provisioned GB with the ability to burst up to 3000 IOPS.

- **Provisioned IOPS**
  
  SSD Storage (io1) is able to provide a user-specified IOPS consistent performance throughout the life-time of the database.
  
     - Optimized for I/O intensive OLTP database workloads.
  
     - Provisioned IOPS can be up to 40,000 IOPS per DB instance.

`5.4.5`

> **Low Adminstration**

- *It comes pre-configured with settings suited for the engine and the selected class*

- **DB Parameters Groups**
  
  Allow for granular control and fine-tuning

- **Automatic Software patching**
  
  with the ability to optionally control it.

`5.4.6`

> **RDS Scaling**

- **Push-button compute scaling**
  
  the ability to scale vertically up or down an instance up to 32 vCPUs and 244 GiB RAM.
  
     - Scaling operations done in few minutes.

- **Easy Storage Scaling**
  
     - Aurora
       
       Automatically scales up in storage to a max of 64TB or the maximum you set.
  
     - Microsoft SQL Server
       
       Automatically scales up to max of 16TB.
  
     - All other engines
       
       Automatically scales up to max of 64TB.

- **READ Replicas**
  
  You can create read replicas of a primary DB instance
  
     - cross AZ.
  
     - cross Region.

`5.5`

> **AWS DynamoDB**
> 
> a serverless non relational database service

- Key-value and document data model, capable of storing tables of any size with horizontal scaling.

- **DAX**
  
  (DynamoDB Accelerator)
  
  [DAX: How it works - Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.concepts.html)

- **DynamoDB Streams**
  
  [DynamoDB Streams Use Cases and Design Patterns | AWS Database Blog](https://aws.amazon.com/blogs/database/dynamodb-streams-use-cases-and-design-patterns/)

`5.5.1`

> **Create a NoSQL Table**

- [Core components of Amazon DynamoDB - Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html) 

- [Using Global Secondary Indexes in DynamoDB - Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html)

`5.5.2`

> **DynamoDB Scans**

- [Working with scans in DynamoDB - Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Scan.html)

- [Scan - Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Scan.html)`

`5.5.3`

> **DynamoDB Query**

- [Query operations in DynamoDB - Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Query.html)

- [Query - Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Query.html)

![Decision diagram which retrieval function to use](https://i.stack.imgur.com/Oq8zM.png)

`5.4,5`

> **AWS RDS** vs. **AWS DynamoDB**
> 
> [Amazon RDS vs DynamoDB: 12 Differences You Should Know](https://cloudacademy.com/blog/amazon-rds-vs-dynamodb-12-differences/)

`5.6`

> **RedShift**
> 
> (Data Warehouse as a Service)

- [Data Lake vs Data Warehouse - Qlik](https://www.qlik.com/us/data-lake/data-lake-vs-data-warehouse)

- [Database vs. Data Warehouse: A Comparative Review](https://www.healthcatalyst.com/insights/database-vs-data-warehouse-a-comparative-review#:~:text=What%20are%20the%20differences%20between,provisions%20them%20for%20analytical%20use.)

- [Normalization in OLTP vs. OLAP: Striking the Balance](https://www.linkedin.com/pulse/normalization-oltp-vs-olap-striking-balance-sumeet-shukla-lwubc/?trk=articles_directory)

`5.7`

> **AWS DocumentDB**
> 
> Document database service that supports MongoDB workloads. (MongoDB is a document database program.)

- [AWS Databases: DynamoDB vs Document DB](https://k21academy.com/amazon-web-services/aws-solutions-architect/aws-dynamodb-vs-document/)

`Module @6`

### SECURITY.

`6.1`

> **AWS Shared Responsibility Model**

- AWS
  
  Responsible of security **of** the cloud.

- You
  
  Responsible of security **in** the cloud.

- it's like a housebuilder and a houseowner. AWS is responsible for constructing your house and ensuring it's solidly built, you need to keep your doors and windows closed and locked. 
  
  *AWS give you the tools to secure yourself and it's up to you use them wisely.*
  
  ![](C:\Users\msal7\AppData\Roaming\marktext\images\2024-02-01-18-41-35-image.png)

`6.2`

> **AWS Inspector**
> 
> A tool to help improve the security and compliance of your AWS deployed applications by running an automated security assessment.

`6.3`

> **AWS GuardDuty**
> 
> a service that provides intelligent threat detection for your AWS infrastructure and resources. It identifies threats by continuously monitoring the network activity and account behavior within your AWS environment.

`Module @7`

### MONITORING AND ANALYTICS.

 `7.1`

> **Monitoring**: 

- Observing systems, Collecting metrics, and then using data to make decisions.

`7.2`

> **AWS CloudWatch**

- Monitor and manage various metrics and configure alarm actions based on data from those metrics.

- **CloudWatch alarms**
  
  Automatically perform actions if a metric beyond a defined threshold.

- **CloudWatch dashboard**
  
  Access all metrics from a central location.
  
  ![](C:\Users\msal7\AppData\Roaming\marktext\images\2024-02-04-21-04-21-image.png)

`7.3`

> **AWS CloudTrail**

- records API calls for your account. The recorded information includes the identity of the API caller, the time of the API call, the source IP address of the API caller,

`Module @8`

### PRICING AND SUPPORT.

`8.1`

> **AWS Consoildated Billing**

- [Consolidated billing for AWS](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html)

`8.2`

> **AWS Budgets**

- set a predefined amount of money, usage, etc.. and a threshold to alert you!

`8.3`

> **AWS Cost Explorer**

- tool that lets you visualize, understand, and manage your AWS costs and usage over time.

`Module @9`

### MIGRATION AND INNOVATION.

`9.1`

> **Migration Complete Overview**

- [What is Migration to the cloud | AWS Cloud Enterprise Startegy Blog](http://amzn.to/considering-mass-migration)

- [A Process for Mass Migrations to the Cloud | AWS Cloud Enterprise Strategy Blog](https://aws.amazon.com/blogs/enterprise-strategy/214-2/)

- [6 Strategies for Migrating Applications to the Cloud | AWS Cloud Enterprise Strategy Blog](https://aws.amazon.com/blogs/enterprise-strategy/6-strategies-for-migrating-applications-to-the-cloud/)

`9.1`

> **AWS CAF**
> 
> (Cloud Adoption Framework)

- [AWS Cloud Adoption Framework](https://aws.amazon.com/professional-services/CAF/)

`Module @10`

### THE CLOUD JOURNEY.

`10.1`

> **AWS Well-Architected Framework**

- [AWS Well-Architected Framework - AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)

`10.2`

> **IAM**
> 
> (Identity and Access Management)

- [What is IAM? - AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
  
  In the left section of the docs, you'll find subarticles under this one.

- [Getting started with IAM - AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started.html)

- [Using AWS Identity and Access Management Access Analyzer - AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)
