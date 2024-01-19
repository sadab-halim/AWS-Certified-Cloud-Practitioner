# Short Notes
## EC2 Instance Storage
- **EBS Volumes**:
	- Network drives attached to one EC2 instance at a time
	- Mapped to an Availability Zones 
	- Can use EBS Snapshots for backups / transferring EBS volumes across AZ
- **AMI**: create ready-to-use EC2 Instances with our customizations
- **EC2 Image Builder**: automatically build, test and distribute AMIs
- **EC2 Instance Store**: 
	- High performance hardware disk attached to our EC2 Instance
	- Lost if our instance is stopped/terminated
- **EFS** : network file system, can be attached to 100s of instances in a region
- **EFS-IA**: cost-optimized storage class for infrequent accessed files
- **FSx for Windows**: network file system for windows servers
- **FSx for Lustre**: high performance computing linux file sys
## ELB & ASG
- **High Availability** vs **Scalability** (vertical and horizontal) vs **Elasticity** vs **Agility** in the Cloud
- **Elastic Load Balancers (ELB)**:
	- Distribute traffic across backend EC2 instances, can be Multi-AZ
	- Supports health checks
	- 4 Types:
		- **Classic (old)**
		- **Application** : HTTP - Layer 7
		- **Network** : TCP - Layer 4
		- **Gateway** : Layer 3
- **Auto Scaling Groups (ASG)**:
	- Implement Elasticity for your application, across multiple AZ
	- Scale EC2 Instances based on the demand on your system, replace unhealthy
	- Integrated with ELB




## Amazon S3
- **Buckets vs Objects** : global unique name, tied to a region
- **S3 Security** : IAM policy, S3 Bucket policy (public access), S3 Encryption
- **S3 Websites** : host a static website on Amazon S3
- **S3 Versioning** : multiple versions for files, prevent accidental deletes
- **S3 Replication** : same-region or cross-region, ing
- **S3 Storage Classes**: Standard IA, IZ-IA, Intelligent, Glacier (Instant, Flexible, Deep)
- **Snow Family**: import data onto S3 through a physical device, edge computing 
- **OpsHub** : desktop application to 
- **Storage Gateway**: hybrid solution to extend on-premises storage to S3



## Databases & Analytics
- **Relational Databases - OLTP**: RDS & Aurora (SQL)
- **Differences between Multi-AZ, Read Replicas, Multi-Region**
- **In-memory Database**: ElastiCache
- **Key/Value Database**: DynamoDB (serverless) & DAX (cache for DynamoDB)
- **Warehouse - OLAP**: Redshift (SQL)
- **Hadoop Cluster**: 
- **Athena**: query data on Amazon S3 (serverless & SQL)
- **boards on your data (serverless)
- **DocumentDB**: Aurora for MongoDB (JSON - NoSQL Database)
- **Amazon QLDB**: Financial Transactions Ledger (immutable journal, cryptographically verifiable)
- **Amazon Managed Blockchain**: managed Hyperledger Fabric & Ethereum blockchains
- **Glue**: Managed ETL (Extract Transform Load) and Data Catalog Service
- **Database Migration**: DMS
- **Neptune**: Graph Database

## Other Compute
- **Docker**: container technology to run applications
- **ECS**:  run Docker containers on EC2 instances
- **Fargate**: 
	- Run Docker containers without provisioning the infrastructure
	- Severless offering (no EC2 instances)
- **ECR**: private docker images repository
- **Barch**: run batch jobs on AWS across managed EC2 instances
- **Lightsail**: predictable & low pricing for simple application & DB stacks

## Lambda
- Lambda is Serverless, Function as a Serivce, seamless scaling, reactive 
- **Lambda Billing**:
	- By the time run x by the RAM provisioned
	- By the number of invocations
- **Language Support**: many programming languages except (arbitrary)
- **Invocation Time**: up to 15 minutes
- **Use cases**:
	- Create thumbnails for images uploaded onto S3
	- Run a serverless cron job
- **API Gateway**: expose Lambda functions as HTTP API

## Deployment
- **CloudFormation** (AWS only):
	- Infrastructure as Code, works with almost all of AWS resources
	- Repeat across regions & accounts	
- **Beanstalk** (AWS only):
	- Platform as a Service (PaaS), limited to certain programming languages or Docker
	- Deploy code consistently with a known architecture: ex, ALB + EC2 + RDS
- **CodeDeploy** (hybrid): deploy & upgrade any application onto servers
- **Systems Manager** (hybrid): patch, configure and run commands at scale
- **OpsWorks** (hybrid): managed Chef and Puppet in AWS

## Developer
- **CodeCommit** : store code in private git repository (version controlled)
- **CodeBuild** : build & test code in AWS
- **CodeDeploy** : deploy code onto servers
- **CodePipeline** : orchestration of pipeline (from code to build to deploy)
- **CodeArtifact** : store software packages / dependencies on AWS 
- **CodeStar** : unified view for allowing developers to do CICD and code
- **Cloud9** : Cloud IDE (Integrated Development Environment) with collab
- **AWS CDK** : define your cloud infrastructure using a programming language

## Global Applications
- **Global DNS: Route 53**
	- Great to route users to the closes deployment with least latency
	- Great for disaster recovery strategies
- **Global Content Delivery Network (CDN): CloudFront**
	- Replicate part of your application to AWS Edge Locations - decrease latency
	- Cache common requests - improved user experience and decreased latency 
- **S3 Transfer Acceleration**:
	- Acceleare global uploads & downloads into Amazon S3
- **AWS Global Accelerator**:
	- Improve global application availability and perfornace using the AWS global network
- **AWS Outposts** : Deploy Outposts Racks in your own Data Centers to extend AWS services
- **AWS WaveLength**:
	- Brings AWS services to the edge of the 5G networks
	- Ultra-low latency applications
- **AWS Local Zones**:
	- Bring AWS resources (compute, database, storage, ..) closer to your users
	- Good for latency-sensitive applications

## Integration
- **SQS**:
	- Queue service in AWS
	- Multiple producers, messages are kept up to 14 days
	- Multiple consumers share the read and delete messages when done
	- Used to decouple applications in AWS
- **SNS**:
	- Notification service in AWS
	- Subscribers: Email, Lambda, SQS, HTTP, Mobile, ...
	- Multipe Subscribers, send all message to  all of them
	- No message retention
- **Kinesis**: real-time data streaming, persistence and analysis
- **Amazon MQ**: managed message broker for ActiveMQ and Rabbit MQ in the cloud (MQTT, AMQP.. protocols)

## Monitoring
- **CloudWatch**
	- **Metrics**: monitor the performance of AWS services and billing metrics
	- **Alarms**: automate notification, perform EC2 action, notify to SNS based on metric
	- **Logs**: collect log files from EC2 instances, servers, Lambda functions..
	- **Events (or EventBridge)**: react to events in AWS, or trigger a rule on a schedule
- **CloudTrail** audit API calls made within your AWS account
- **CloudTrail Insights**: automated analysis of your CloudTrail Events
- **X-Ray**: trace requests made through your distributed applications
- **AWS Health Dashboard**: status of all AWS services across all regions
- **AWS Account Health Dashboard**: AWS events that impact your infrastructure 
- **Amazon CodeGuru**: automated code reviews and application performance recommendations
	
## VPC
- **VPC**: Virtual Private Cloud
- **Subnets**: tied to an AZ, network partition of the VPC
- **Internet Gateway**: at the VPC level, provide Internet Access
- **NAT Gateway/Instances**: give internet 
- **NACL**: stateless, subnet rules for inbound and outbound
- **Security Groups**: stateful, operate at the EC2 instance level or ENI
- **VPC Peering**: connect two VPC with non overlapping IP ranges, nontransitive
- **Elastic IP**: fixed public IPvr, ongoing cost if not in-use
- **VPC Endpoints**: provide private access to AWS services within VPC
- **PrivateLink**: privately connect to a service in a 3rd party VPC
- **VPC Flow Logs**: network traffic logs
- **Site to Site VPN**: VPN over public internet between on-premises DC and AWS
- **Client VPN**: OpenVPN connection from your computer into your VPC
- **Direct Connect**: direct private connection to AWS
- **Transit Gateway**: connect thousands of VPC and on-premises networks together

## Security & Compliance
- **Shared Responsibility on AWS**
- **Shield**: automatic DDoS protection + 24/7 support for advanced
- **WAF**: firewall to filter incoming requests based on rules
- **KMS**: encryption keys managed by AWS
- **CloudHSM**: hardware encryption, we manage encryption keys
- **AWS Certificate Manager**: provision, manage, and deploy SSL/TLS Certificates
- **Artifact**: get access to compliance reports such as PCI, ISO, etc
- **GuardDuty**: find malicious behaviour with VPC, DNS & CloudTrail Logs
- **Inspector**: find software vulnerabilities in EC2, ECR Images, and Lambda functions
- **Network Firewall**: protect VPC against network attacks
- **Config**: track config changes and compliance against rules
- **Macie**: find sensitive data (ex: PII data) in Amazon S3 buckets
- **CloudTrail**: track API cals made by users within account
- **AWS Security Hub**: gather security findings from multiple AWS accounts
- **Amazon Detective**: find the root cause of security issues or suspicious activities
- **AWS Abuse**: report AWS resources used for abusive or illegal purposes 
- **Root user privileges**:
	- Change account settings
	- Close your AWS account
	- Change or cancel your AWS Support Plan
	- Register as a seller in the Reserved Instance Marketplace
- **IAM Access Analyzer**: identify which resources are shared externally

## Machine Learning
- **Rekognition**: face detection, labeling, celebrity recognition
- **Transcribe**: audio to text (ex: subtitles)
- **Polly**: text to audio
- **Translate**: translations
- **Lex**: build conversatinoal bots - chatbots
- **Connect**: cloud contact center
- **Comprehend**: natural language processing
- **SageMaker**: machine learning for every developer and data scientist
- **Forecast**: build highly accurate forecasts
- **Kendra**: ML-powered search engine
- **Personalize**: real-time personalized recommendations
- **Textract**: detect text and data in documents

## Account Best Practices
- Opeare multiple accounts using **Organizations**
- Use **SCP** (service control policies) to restrict account power
- Easily setup multiple accounts with best-practices with **AWS Control Tower**
- **Use Tags & Cost Allocation Tags** for easy management & billing
- **IAM guidelines**: MFA, least-privilege, password policy, password rotation
- **Config**: to record all resources configurations & compliance over time
- **CloudFormation**: to deploy stacks across accounts and regions
- **Trusted Advisor**: to get insights, Support Plan adapted to your needs
- Send Service Logs and Access Logs to **S3 or CloudWatch Logs**
- **CloudTrail** to record API calls made within your account
- **If your account is compromised**: change the root password, delete and rotate all password/keys, contact the AWS support
- Allow uses to create pre-defined stacks defined by admins using **AWS Service Catalog**

## Billing and Costing Tools
- **Compute Optimizer**: recommends resources' configurations to reduce cost
- **Pricing Calculator**: cost of services on AWS
- **Billing Dashboard**: high level overview + free tier dashboard
- **Cost Allocation Tags**: tag resources to create detailed reports
- **Cost and Usage Reports**: most comprehensive billing dataset
- **Cost Explorer**: view current usage (detailed) and forecast usage
- ** Billing Alarms**: in us-east-1 -- track overal and pre-service billing
- **Budgets**: more advanced -- track usage, coss, RI, and get alerts
- **Savings Plans**: easy way to save based on long-term usage of AWS
- **Cost Anomaly Detection**: detect unusual spends using Machine Learning
- **Service Quotas**: notify you when you're close to service quota thresold

## Advanced Identity
- **IAM**:
	- Identity and Access Management inside your AWS account
	- For users that you trust and belong to your company
- **Organizations**: manage multiple accounts
- **Security Token Service (STS)**: temporary, limited-privileges credentials to access AWS resources
- **Cognito**: create a database of users for your mobile & web applications
- **Directory Services**: integrate Microsoft Active Directory in AWS
- **IAM Identity Center**: one login for multiplebhvhvhjv AWS accounts & applications



