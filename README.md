# ISV Plug 'n Play

Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. Amazon RDS offloads the undifferentiated heavy lifting of keeping the lights on by automating time-consuming administration tasks such as hardware provisioning, database setup, patching, and backups. Amazon RDS frees ISV Startups to focus on higher-level efforts such as performance tuning, schema design, and developing new application features.

The ISV Plug 'n Play program consists of a packaged bundle that ISV Startups can leverage to accelerate the creation of a new RDS enviornment using baked in best practices.


![alt text](https://github.com/aws-samples/amazon-isv-plug-n-play/blob/main/ISVPnPRefArch.jpg?raw=true)

The sample CloudFormation templates provision the network infrastructure and all the components shown in the architecture diagram. I broke the CloudFormation templates into the following three stacks.

1. CloudFormation template to set up VPC, subnets, route tables, internet gateway, NAT gateway, S3 gateway endpoint, AWS Secrets Manager interface endpoint, and other networking components.
    
2. CloudFormation template to set up an Amazon Linux bastion host in an Auto Scaling group to connect to the Aurora PostgreSQL DB cluster.
    
3. CloudFormation template to set up Aurora PostgreSQL DB cluster with master user password stored in AWS Secrets Manager and bootstrap the database using AWS Lambda.

The stacks are integrated using exported output values. Using three different CloudFormation stacks instead of one nested stack gives you some flexibility. For example, you can choose to deploy the VPC and bastion host CloudFormation stacks once and Aurora PostgreSQL DB cluster CloudFormation stack multiple times in an AWS Region.

