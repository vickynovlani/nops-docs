---
title: Adding Multiple AWS Account to nOps with CloudFormation
parent: Getting Started
nav_order: 6
layout: default
---

# Adding Multiple AWS Account to nOps with CloudFormation #

## IAM Policy for nOps Platform ##

nOps requires safe, secure, and AWS-approved cross account access to your AWS accounts in order to give you the analysis, dashboards, and reports that you need. We only see what you want us to see in order to provide our services, no more, and we need you to give us permission first.

**For AWS Payer/Management Account, nOps uses the following policies:**

1.  AWS managed [ReadOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/ReadOnlyAccess) policy, which is completely managed by AWS and is updated periodically as AWS adds new services.
2.  Since the AWS managed ReadOnlyAccess policy contains some read access to sensitive data, nOps uses an explicit deny list which can be easily update for your own security requires. – [Explicit Deny List](#h_6b41a85df4)
3.  Lastly, few other policies that are necessary to create the Cost and Usage Report for Cost Visibility, Well-Architected Review and placeholders to support automating the setup for nOps ShareSave Program. [CUR](https://docs.nops.io/en/articles/4886159-aws-iam-policy-nops-free-platform#h_b477ab632a) , [S3](https://docs.nops.io/en/articles/4886159-aws-iam-policy-nops-free-platform#h_ea6fb820c6), [Well-Architected](#h_a8e83c44fd) , [EventBridge](#h_a97b55384c) and [Organization](#h_9bd655b8ac),

**For the AWS Linked accounts, nOps uses the following policies:**

1.  AWS managed [ReadOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/ReadOnlyAccess) policy, which is completely managed by AWS and is updated periodically as AWS adds new services.
2.  Since the AWS managed ReadOnlyAccess policy contains some read access to sensitive data, nOps uses an explicit deny list which can be easily update for your own security requires. – [Explicit Deny List](#h_6b41a85df4)
3.  Lastly, few other policies that are necessary for Well-Architected Review and placeholders to automating the setup for nOps ShareSave Program. [Well-Architected](#h_a8e83c44fd) and [EventBridge](https://docs.nops.io/en/articles/4886159-aws-iam-policy-nops-free-platform#h_a97b55384c)

**Payer Account – IAM Policy JSON – [Payer Account – JSON](https://docs.nops.io/en/articles/4886159-aws-iam-policy-nops-free-platform#h_15aac0483e)

**Linked Account – IAM Policy JSON – [Linked Account – JSON](#h_f64f433714)

What? Why? and How Much?
========================

The following tables describe each permission within the IAM policy:

* First column: Permission name.
* Second column: What the permission is?
* Third column: Why the permission is important for nOps?
* Forth column: What kind of access the permission gives to nOps?What? Why? and How Much?The following tables describe each permission within the IAM policy:
    * First column: Permission name.
    * Second column: What the permission is?
    * Third column: Why the permission is important for nOps?
    * Forth column: What kind of access the permission gives to nOps?

|     |     |     |     |
| --- | --- | --- | --- |
| CUR | What | Why | Access (Full: Read, Limited: Write) |
| DescribeReportDefinitions | Lists the AWS Cost and Usage Report available to this account. | Used for creating reports in billing bucket setup. | Read: All resource |
| PutReportDefinition | Creates a new report using the description that you provide. | Used for creating reports in billing bucket setup. | Write: All resource |

|     |     |     |     |
| --- | --- | --- | --- |
| EventBridge | **What** | **Why** | **Access(Limited: Write)** |
| CreateEventBus | Creates a new event bus within your account. | Allows nOps to create EventBridge integrations for automation. Required for ShareSave program. | Write: All resources |

|     |     |     |     |
| --- | --- | --- | --- |
| **Organizations** | **What** | **Why** | **Access (Limited: Write, Full: List, Read)** |
| InviteAccountToOrganization | Sends an invitation to another AWS account, asking it to join your organization as a member account. | Required for onboarding child accounts via CloudFormation stack during Automatic Setup and the ShareSave program. | Write: All resources |

|     |     |     |     |
| --- | --- | --- | --- |
| S3  | What | Why | Access (Limited: Read) |
| HeadBucket | Allows you to determine if a bucket exists and you have permission to access it. | This permission allows nOps to see if the butcket for CUR already exists or do we need need to create one. | Read |
| HeadObject | The HEAD action retrieves metadata from an object without returning the object itself | This permission allows nOps to only see the metadata of a bucket without allowing nOps to see the bucket’s contents. | Read |

|     |     |     |     |
| --- | --- | --- | --- |
| Support | What | Why | Access (Limited: Read) |
| DescribeTrustedAdvisorCheckRefreshStatuses | Returns the refresh status of the AWS Trusted Advisor checks that have the specified check IDs. | Not used anymore. | Read: All resources |
| DescribeTrustedAdvisorCheckResult | Returns the results of the AWS Trusted Advisor check that has the specified check ID. | Not used anymore. | Read: All resources |
| DescribeTrustedAdvisorChecks | Returns information about all available AWS Trusted Advisor checks, including the name, ID, category, description, and metadata. | Not used anymore. | Read: All resources |

|     |     |     |     |
| --- | --- | --- | --- |
| Well-Architected | What | Why | Access (Full access) |
| wellarchitected | Gives full access to Well-Architected. | nOps provides a full functionality dedicated for wellarchitected compliances and it requires full access of this component for managing cloud workloads. | Full access |

## Explicit Deny ##
=============

The following is the list of services for which nOps explicitly denies the permission:

* [ACM (AWS Certificate Manager)](#h_3bc9b873e6)
* [API Gateway](#h_e838497cf4)
* [AppConfig](#h_d0d3c85d0e)
* [AppFlow](#h_3670bf11c6)
* [AppStream](#h_1d0897b456)
* [AppSync](#h_3056e2a187)
* [Athena](#h_31228a7ae4)
* [Backup](#h_11ae28a6d8)
* [Cassandra](#h_74fc83cbd4)
* [Chime](#h_7a41c3d9cb)
* [Cloud9](#h_98e96e885a)
* [Cloud Directory](#h_95fd28b23c)
* [CloudFront](#h_fe9615df4a)
* [CloudWatch](#h_66879e9ef9)
* [CodeArtifact](#h_a01a236a15)
* [CodeBuild](#h_ffe9aaefae)
* [CodeCommit](#h_7b21d6094a)
* [CodeDeploy](#h_138527bcc1)
* [CodeStar](#h_7d721b72cc)
* [Cognito](#h_94b367841c)
* [Comprehend](#h_abc33df1ab)
* [Config](#h_46f3327be8)
* [Connect](#h_9410cfbea1)
* [Data Pipeline](#h_83f9a453c3)
* [DAX (DynamoDB Accelerator)](#h_b29691cecf)
* [DeepComposer](#h_2e59524121)
* [Device Farm](#h_dbc52636c7)
* [Direct Connect](#h_e9e8656e9a)
* [Discovery](#h_759cffb126)
* [DMS (Database Migration Service)](#h_4f5cc1751e)
* [DS (Directory Service)](#h_608672ba01)
* [DynamoDB](#h_847ad5fdd6)
* [EC2 (Elastic Compute Cloud)](#h_47cd293cb4)
* [ECR (Elastic Container Registry)](#h_a15540c6d5)
* [EKS (Elastic Kubernetes Service)](#h_a6fc93988f)
* [Elastic Beanstalk](#h_3a34cf5c99)
* [ES (Elasticsearch)](#h_bd826b241b)
* [FIS (Fault Injection Simulator)](#h_a12bd5feb9)
* [FMS (Firewall Manager)](#h_a66c6f7e3f)
* [Fraud Detector](#h_bb1dad8fef)
* [GameLift](#h_d2f8aeba8d)
* [GeoLocation](#h_b94f4804cb)
* [Glue](#h_7f6ff4c556)
* [GuardDuty](#h_54da457b21)
* [Inspector 2](#h_96959ee43b)
* [Image Builder](#h_5194c096cd)
* [IoT RoboRunner](#h_b14f3fd365)
* [IoT SiteWise](#h_e930a951a9)
* [IVS (Interactive Video Service)](#h_958a42931d)
* [Kafka](#h_fe8658ce0d)
* [Kendra](#h_17a4be0102)
* [Kinesis](#h_c7c9156b07)
* [KMS (Key Management Service)](#h_a7b3044a3c)
* [Lex](#h_7e157be561)
* [Lambda](#h_ddbd7cab9e)
* [License Manager](#h_da0cae0af9)
* [Lightsail](#h_3038682523)
* [Logs](#h_cbd27ecccf)
* [ML (Machine Learning)](#h_45b3b7ff51)
* [Macie2](#h_582de2ad2a)
* [Mobile Hub](#h_1711c2c8c4)
* [Nimble](#h_0e7ca0498f)
* [Polly](#h_a79354c210)
* [Proton](#h_86152e4826)
* [QLDB (Quantum Ledger Database)](#h_f71ed37abd)
* [RDS (Relational Database Service)](#h_71c124d68d)
* [Rekognition](#h_0ec0f1ef88)
* [Resilience Hub](#h_2277760ff9)
* [RoboMaker](#h_e32d2a35d9)
* [S3 (Simple Storage Service)](#h_a731e9d832)
* [SageMaker](#h_89f6ec7cd3)
* [Schemas](#h_021ce2ad28)
* [SDB (SimpleDB)](#h_4017a690f1)
* [Secrets Manager](#h_592707b0fb)
* [Security Hub](#h_c0d12878e6)
* [SES (Simple Email Service)](#h_be0d5553cf)
* [Signer](#h_a96ec592e0)
* [SMS (Server Migration Service)](#h_26f0ea1fff)
* [Snowball](#h_3679130b9f)
* [SQS (Simple Queue Service)](#h_f6b7a96980)
* [S SM (Systems Manager Agent)](#h_73cc22120f)
* [SSO (Single Sign-On)](#h_2bc317efc6)
* [Storage Gateway](#h_e9af2fdcd1)
* [Support](#h_ad51435ead)
* [TimeStream](#h_c1dceceb6c)
* [Transcribe](#h_90a2569550)
* [Transfer](#h_20f9239d39)
* [WAF (Web Application Firewall)](#h_1d50ab4444)
* [WorkMail](#h_bfe2bec5c8)

|     |     |
| --- | --- |
| ACM (AWS Certificate Manager) | What |
| acm-pca:Describe | Denies all Describe permissions in ACM-PCA. |
| acm-pca:Get | Denies all Get permissions in ACM-PCA. |
| acm-pca:List | Denies all List permissions in ACM-PCA. |
| acm:Describe | Denies all Describe permissions in ACM. |
| acm:Get | Denies all Get permissions in ACM. |
| acm:List | Denies all List permissions in ACM. |

|     |     |
| --- | --- |
| API Gateway | What |
| GET | Denies all Get permission for API Gateway. |

|     |     |
| --- | --- |
| AppConfig | What |
| GetConfiguration | Denies the permission to view details about a configuration. |

|     |     |
| --- | --- |
| AppFlow | What |
| DescribeConnector | Denies the permission to describe a connector registered in Amazon AppFlow. |
| ListConnector | Denies the permission to list connectors supported in Amazon AppFlow. |

|     |     |
| --- | --- |
| AppStream | What |
| DescribeDirectoryConfigs | Denies the permission to retrieve a list that describes one or more specified Directory Config objects for AppStream 2.0. |
| DescribeUsers | Denies the permission to retrieve a list that describes one or more specified users in the user pool. |
| DescribeSessions | Denies the permission to retrieve a list that describes the streaming sessions for a specified stack and fleet. |

|     |     |
| --- | --- |
| AppSync | What |
| Get | Denies the permission to read resources in this service. |
| List | Denies the permission to list resources in this service. |

|     |     |
| --- | --- |
| Athena | What |
| Get | Denies the permission to read resources in this service. |
| List | Denies the permission to list resources in this service. |

|     |     |
| --- | --- |
| Backup | What |
| GetBackupVaultAccessPolicy | Denies the permission to get backup vault access policy. |

|     |     |
| --- | --- |
| Cassandra (Keyspaces) | What |
| Select | Denies the permission to SELECT data from table. |

|     |     |
| --- | --- |
| Chime | What |
| Describe | Denies the permission to read resources in this service. |
| Get | Denies the permission to read resources in this service. |
| List | Denies the permission to list resources in this service. |

|     |     |
| --- | --- |
| Cloud9 | What |
| Describe | Denies the permission to read resources in this service. |
| Get | Denies the permission to read resources in this service. |
| List | Denies the permission to read resources in this service. |

|     |     |
| --- | --- |
| Cloud Directory | What |
| Get | Denies the permission to read resources in this service. |
| List | Denies the permission to list resources in this service. |

|     |     |
| --- | --- |
| CloudFront | What |
| GetCloudFrontOriginAccessIdentity | Denies the permission to get the information about a cloud front origin access identity. |
| GetFieldLevelEncryption | Denies the permission to get the field-level encryption configuration information. |
| GetKeyGroupConfig | Denies the permission to get a key group configuration. |

|     |     |
| --- | --- |
| CloudWatch | What |
| GetMetricData | Denies the permission to retrieve batch amounts of CloudWatch metric data and perform metric math on retrieved data. |
| GetMetricStream | Denies the permission to return the details of a CloudWatch metric stream. |
| ListMetricStreams | Denies the permission to return a list of all CloudWatch metric streams in your account. |

|     |     |
| --- | --- |
| CodeArtifact | What |
| GetAuthorizationToken | Denies the permission to generate a temporary authorization token for accessing repositories in a domain. |
| ReadFromRepository | Denies the permission to return package assets and metadata from a repository endpoint. |

|     |     |
| --- | --- |
| CodeBuild | What |
| BatchGet | Denies the permission to all BatchGet permissions. |
| ListSourceCredentials | Denies the permission to return a list of SourceCredentialsInfo objects. |

|     |     |
| --- | --- |
| CodeCommit | What |
| BatchGet | Denies the permission to all BatchGet permissions. |
| Get | Denies the permission to Get permissions. |
| GitPull | Denies the permission to pull information from an AWS CodeCommit repository to a local repo. |

|     |     |
| --- | --- |
| CodeDeploy | What |
| BatchGet | Denies the permission to all BatchGet permissions. |
| Get | Denies the permission to Get permissions. |

|     |     |
| --- | --- |
| CodeStar | What |
| DescribeUserProfile | Denies the permission to describe a user in AWS CodeStar and the user attributes across all projects. |
| ListUserProfiles | Denies the permission to list user profiles in AWS CodeStar. |

|     |     |
| --- | --- |
| Cognito | What |
| cognito-identity (Cognito Identity) | Denies the permission to access any resources in this service. |
| cognito-idp (Cognito User Pools) | Denies the permission to access any resources in this service. |
| cognito-sync (Cognito Sync) | Denies the permission to access any resources in this service. |

|     |     |
| --- | --- |
| Comprehend | What |
| Describe | Denies the permission to Describe resources. |
| List | Denies the permission to List resources. |

|     |     |
| --- | --- |
| Config | What |
| BatchGetAggregateResourceConfig | Denies the permission to return the current configuration items for resources that are present in your AWS Config aggregator. |
| BatchGetResourceConfig | Denies the permission to return the current configuration for one or more requested resources. |
| SelectAggregateResourceConfig | Denies the permission to accept a structured query language (SQL) SELECT command and an aggregator to query configuration state of AWS resources across multiple accounts and regions, performs the corresponding search, and returns resource configuration matching the properties. |
| SelectResourceConfig | Denies the permission to accept a structured query language (SQL) SELECT command, performs the corresponding search, and returns resource configurations matching the properties. |

|     |     |
| --- | --- |
| Connect | What |
| Describe | Denies the permission to Describe resources |
| Get | Denies the permission to Get resources. |
| List | Denies the permission to List resources. |

|     |     |
| --- | --- |
| Data Pipeline | What |
| DescribeObjects | Denies the permission to get the object definitions for a set of objects associated with the pipeline. |
| EvaluateExpression | Denies the permission to task runners to call EvaluateExpression, to evaluate a string in the context of the object. |
| QueryObjects | Denies the permission to query the specified pipeline for the names of the objects that match the specified set of conditions. |

|     |     |
| --- | --- |
| DAX (DynamoDB Accelerator) | What |
| BatchGetItem | Denies the permission to return the attributes of one or more items from one or more tables. |
| GetItem | Denies the permission to the GetItem operation that returns a set of attributes for the item with the given primary key. |
| Query | Denies the permission to use the primary key of a table or a secondary index to directly access items from that table or index. |

|     |     |
| --- | --- |
| DeepComposer | What |
| Get | Denies all Get permissions in DeepComposer. |
| List | Denies all List permissions in DeepComposer. |

|     |     |
| --- | --- |
| Device Farm | What |
| GetRemoteAccessSession | Denies the permission to retrieve the link to a currently running remote access session. |
| ListRemoteAccessSessions | Denies the permission to list the information of currently running remote access sessions. |

|     |     |
| --- | --- |
| Direct Connect | What |
| Describe | Denies all Describe permissions in Direct Connect. |
| List | Denies all List permissions in Direct Connect. |

|     |     |
| --- | --- |
| Discovery | What |
| Describe | Denies all Describe permissions in Discovery. |
| Get | Denies all Get permissions in Discovery. |
| List | Denies all List permissions in List. |

|     |     |
| --- | --- |
| DMS (Database Migration Service) | What |
| Describe | Denies all DEscribe permissions in DMS. |
| List | Denies the permission to list all tags for AWS DMS resources. |

|     |     |
| --- | --- |
| DS (Directory Service) | What |
| Get | Denies all Get permission in Directory Service. |

|     |     |
| --- | --- |
| DynamoDB | What |
| GetItem | Denies permission to the GetItem operation that returns a set of attributes for the item with the given primary key. |
| BatchGetItem | Denies permission to return the attributes of one or more items from one or more tables. |
| Query | Denies permission to use the primary key of a table or a secondary index to directly access items from that table or index. |
| Scan | Denies the permission to return one or more items and item attributes by accessing every item in a table or a secondary index. |

|     |     |
| --- | --- |
| EC2 (Elastic Compute Cloud) | What |
| GetConsoleScreenshot | Denies the permission to retrieve a JPG-format screenshot of a running instance. |

|     |     |
| --- | --- |
| ECR (Elastic Container Registry) | What |
| ecr:BatchGetImage | Denies the permission to get detailed information for specified images within a specified repository. |
| ecr:GetAuthorizationToken | Denies the permission to retrieve a token that is valid for a specified registry for 12 hours. |
| ecr:GetDownloadUrlForLayer | Denies the permission to retrieve that download URL corresponding to an image layer. |
| ecr-public:GetAuthorizationToken | Denies the permission to retrieve a token that is valid for a specified registry for 12 hours. |

|     |     |
| --- | --- |
| EKS (Elastic Kubernetes Service) | What |
| DescribeIdentityProviderConfig | Denies the permission to retrieve descriptive information about an Idp config associated with a cluster. |

|     |     |
| --- | --- |
| Elastic Beanstalk | What |
| DescribeConfigurationOptions | Denies the permission to retrieve descriptions of environment configuration options. |
| DescribeConfigurationSettings | Denies the permission to retrieve a description of the settings for a configuration set. |

|     |     |
| --- | --- |
| ES (OpenSearch Service) | What |
| ESHttpGet | Denies the permission to send HTTP GET request to the OpenSearch APIs. |

|     |     |
| --- | --- |
| FIS (Fault Injection Simulator) | What |
| GetExperimentTemplate | Denies the permission to retrieve an AWS FIS Experiment Template. |

|     |     |
| --- | --- |
| FMS (Firewall Manager) | What |
| GetAdminAccount | Denies the permission to retrieve the AWS Organization master account that is associated with AWS Firewall Manager as the AWS Firewall Manager administrator. |

|     |     |
| --- | --- |
| Fraud Detector | What |
| BatchGetVariable | Denies the permission to get a batch of variables. |
| Get | Denies all Get permission in Fraud Detector. |

|     |     |
| --- | --- |
| GameLift | What |
| GetGameSessionLogUrl | Denies the permission to retrieve the location of stored logs for a game session. |
| GetInstanceAccess | Denies the permission to request remote access to a specified fleet instance. |

|     |     |
| --- | --- |
| GeoLocation (Location) | What |
| ListDevicePositions | Denies the permission to retrieve a list of devices and their latest positions from the given tracker resource. |

|     |     |
| --- | --- |
| Glue | What |
| GetSecurityConfiguration | Denies the permission to retrieve a security configuration. |
| SearchTables | Denies the permission to retrieve the tables in the catalog. |
| GetTable | Denies all GetTable permission in Glue. |

|     |     |
| --- | --- |
| GuardDuty | What |
| GetIPSet | Denies the permission to retrieve GuardDuty IPSets |
| GetMasterAccount | Denies the permission to retrieve details of the GuardDuty administrator account associated with a member account. |
| GetMembers | Denies the permission to retrieve the member accounts associated with an administrator account. |
| ListMembers | Denies the permission to retrieve a list of GuardDuty member accounts associated with an administrator account. |
| ListOrganizationAdminAccounts | Denies the permission to list details about the organization delegated administrator for GuardDuty. |

|     |     |
| --- | --- |
| Inspector 2 | What |
| GetConfiguration | Denies the permission to retrieve information about the Amazon Inspector configuration settings for an AWS account. |

|     |     |
| --- | --- |
| Image Builder | What |
| GetImage | Denies the permission to get an EC2 image. |

|     |     |
| --- | --- |
| IoT RoboRunner | What |
| Get | Denies all Get permission in IoT RoboRunner. |

|     |     |
| --- | --- |
| IoT SiteWise | What |
| ListAccessPolicies | Denies the permission to lit all access policies for an identity or a resource. |

|     |     |
| --- | --- |
| IVS (Interactive Video Service) | What |
| GetPlaybackKeyPair | Denies the permission to get the playback keypair information for a specified ARN. |
| GetStreamSession | Denies the permission to get information about the stream session on a specified channel. |

|     |     |
| --- | --- |
| Kafka (MSK) | What |
| GetBootstrapBrokers | Denies the permission to get connection details for the brokers in an MSK cluster. |

|     |     |
| --- | --- |
| Kendra | What |
| Query | Denies the permission to query documents and faqs. |

|     |     |
| --- | --- |
| Kinesis | What |
| Get | Denies all Get permission in Kinesis. |

|     |     |
| --- | --- |
| KMS (Key Management Service) | What |
| DescribeKey | Denies the control to the permission to view detailed information about an AWS KMS key. |
| GetPublicKey | Denies the control to the permission to download the public key of an asymmetric AWS KMS Key. |

|     |     |
| --- | --- |
| Lex | What |
| Get | Denies all Get permission in Lex. |

|     |     |
| --- | --- |
| Lambda | What |
| GetFunctionConfiguration | Denies the permission to view details about the version-specific settings of an AWS Lambda function or version. |

|     |     |
| --- | --- |
| License Manager | What |
| GetGrant | Denies the permission to get a grant. |
| GetLicense | Denies the permission to get a license. |
| ListTokens | Denies the permission to list tokens. |

|     |     |
| --- | --- |
| Lightsail | What |
| GetBucketAccessKeys | Denies the permission to get the existing access key IDs for the specified Amazon Lightsail bucket. |
| GetCertificates | Denies the permission to view information about one or more Amazon Lightsail SSL/TLS certificates. |
| GetContainerImages | Denies the permission to view the container images that are registered to your Amazon Lightsail container service. |
| GetKeyPair | Denies the permission to get information about a key pair. |
| GetRelationalDatabaseLogStreams | Denies the permission to get the log streams available for a relational database. |

|     |     |
| --- | --- |
| Logs | What |
| GetLogEvents | Denies the permission to list log events from the specified log stream. |
| StartQuery | Denies the permission to schedule a query of a log group using CloudWatch Logs Insights. |

|     |     |
| --- | --- |
| ML (Machine Learning) | What |
| GetMLModel | Denies the permission to return an MLModel that includes detailed metadata, and data source information as well as the current status of the MLModel. |

|     |     |
| --- | --- |
| Macie2 | What |
| GetAdministratorAccount | Denies the permission to retrieve information about the Amazon Macie administrator account for an account. |
| GetMember | Denies the permission to retrieve information about an account that’s associated with an Amazon Macie administrator account. |
| GetMacieSession | Denies the permission to retrieve information about the status and configuration settings for an Amazon Macie account. |
| SearchResources | Denies the permission to retrieve statistical data and other information about AWS resources that Amazon MAcie monitors and analyzes. |
| GetSensitiveDataOccurrences | Denies the permission to retrieve occurrences of sensitive data reported by a finding. |

|     |     |
| --- | --- |
| Mobile Hub | What |
| ExportProject | Denies the permission to export the project configuration. |

|     |     |
| --- | --- |
| Nimble Studio | What |
| GetStreamingSession | Denies the permission to get a streaming session. |

|     |     |
| --- | --- |
| Polly | What |
| SynthesizeSpeech | Denies the permission to synthesize speech. |

|     |     |
| --- | --- |
| Proton | What |
| GetEnvironmentTemplate | Denies the permission to describe an environment template. |
| GetServiceTemplate | Denies the permission to describe a service template. |
| ListServiceTemplates | Denies the permission to list service templates. |
| ListEnvironmentTemplates | Denies the permission to list environment templates. |

|     |     |
| --- | --- |
| QLDB (Quantum Ledger Database) | What |
| GetBlock | Denies the permission to retrieve a block from a ledger for a given BlockAddress. |
| GetDigest | Denies the permission to retrieve a digest from a ledger from a given BlockAddress. |

|     |     |
| --- | --- |
| RDS (Relational Database Service) | What |
| Download | Denies all Download permission for RDS. |

|     |     |
| --- | --- |
| Rekognition | What |
| CompareFaces | Denies the permission to compare faces in the source input images with each face detected in the target input image. |
| Detect | Denies all Detect permissions in Rekognition. |
| Search | Denies all Search permission in Rekognition. |

|     |     |
| --- | --- |
| Resilience Hub | What |
| DescribeAppVersionTemplate | Denies the permission to describe the application version template. |
| ListRecommendationTemplates | Denies the permission to list recommendation templates. |

|     |     |
| --- | --- |
| RoboMaker | What |
| GetWorldTemplateBody | Denies the permission to get the body of a world template. |

|     |     |
| --- | --- |
| S3 (S3 Object Lambda) | What |
| s3-object-lambda:GetObject | Denies the permission to retrieve objects from Amazon S3. |

|     |     |
| --- | --- |
| SageMaker | What |
| Search | Denies the permission to search for SageMaker objects. |

|     |     |
| --- | --- |
| Schemas (EventBridgeSchemas) | What |
| GetDiscoveredSchema | Denies the permission to retrieve a schema for the provided list of sample events. |

|     |     |
| --- | --- |
| SDB (SimpleDB) | What |
| Get | Denies all Get permissions for SDB. |
| Select | Denies all Select permissions for SDB. |

|     |     |
| --- | --- |
| Secrets Manager | What |
| *   | Denies all permission in Secrets Manager. |

|     |     |
| --- | --- |
| Security Hub | What |
| GetFindings | Denies the permission to retrieve a list of findings from Security Hub. |
| GetMembers | Denies the permission to retrieve the details of Security Hub member accounts. |
| ListMembers | Denies the permission to retrieve details about Security Hub member accounts associated with the administrator account. |

|     |     |
| --- | --- |
| SES (SES v1, SES v2) | What |
| GetTemplate | Denies the permission to return the template object, which includes the subject line, HTML part, and text part for the template you specify. |
| GetEmailTemplate | Denies the permission to return the template object, which includes the subject line, HTML part, and text part for the template you specify. |
| GetContact | Denies the permission to return a contact from a contact list. |
| GetContactList | Denies the permission to return contact list metadata. |
| ListTemplates | Denies the permission to list the email templates present in your account. |
| ListEmailTemplates | Denies the permission to list all of the email templates for your account. |
| ListVerifiedEmailAddresses | Denies the permission to list all of the email addresses that have been verified. |

|     |     |
| --- | --- |
| Signer | What |
| GetSigningProfile | Denies the permission to return information about a specific Signing Profile. |
| ListProfilePermissions | Denies the permission to list the cross-account permissions associated with a Signing Profile. |
| ListSigningProfiles | Denies the permission to list all Signing Profiles in your account. |

|     |     |
| --- | --- |
| SMS (Pinpoint SMS Voice V2) | What |
| sms-voice:DescribeKeywords | Denies the permission to describe the keywords for a pool or origination phone number. |
| sms-voice:DescribeOptedOutNumbers | Denies the permission to describe the destination phone numbers in an opt-out list. |
| sms-voice:DescribePhoneNumbers | Denies the permission to describe the origination phone numbers in your account. |
| sms-voice:DescribePools | Denies the permission to describe the pools in your account. |

|     |     |
| --- | --- |
| Snowball | What |
| Describe | Denies all Describe permission for Snowball. |

|     |     |
| --- | --- |
| SQS (Simple Queue Service) | What |
| Receive | Denies all Receive permission in SQS. |

|     |     |
| --- | --- |
| S SM (Systems Manager) | What |
| ssm-contacts:* |     |
| ssm:DescribeParameters | Denies the permission to view details about a specified SSM parameter. |
| ssm:GetParameter | Denies all GetParameter permission in Systems Manager. |

|     |     |
| --- | --- |
| SSO (Single Sign-On) | What |
| Describe | Denies all Describe permissions in SSO. |
| Get | Denies all Get permissions in SSO. |
| List | Denies all List permissions in SSO. |

|     |     |
| --- | --- |
| Storage Gateway | What |
| DescribeChapCredentials | Denies the permission to get an array of Challenge-Handshake Authentication Protocol (CHAP) credentials information for a specified iSCSI target, one for each target-initiator pair. |

|     |     |
| --- | --- |
| Support | What |
| DescribeCommunications | Denies the permission to return the communications and attachments for one or more AWS Support cases. |

|     |     |
| --- | --- |
| TimeStream | What |
| ListDatabases | Denies the permission to list databases in your account. |
| ListTables | Denies the permission to list tables in your account. |

|     |     |
| --- | --- |
| Transcribe | What |
| Get | Denies all Get permission in Transcribe. |
| List | Denies all List permission in Transcribe. |

|     |     |
| --- | --- |
| Transfer | What |
| Describe | Denies all Describe permission in Transfer. |
| List | Denies all List permission in Transfer. |

|     |     |
| --- | --- |
| WAF (WAF Regional) | What |
| waf-regional:GetChangeToken | Denies the permission to retrieve a change token to use in create, update, and delete requests. |

|     |     |
| --- | --- |
| WorkMail | What |
| DescribeUser | Denies the permission to read details for a user. |
| GetMailUserDetails | Denies the permission to get the details of the user’s mailbox and account. |
| ListUsers | Denies the permission to list the organization’s users. |

IAM policy for nOps _Last Updated: 12/17/2022_

**Payer Account – IAM Policy JSON**
-----------------------------------
```json
 {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "cur:DescribeReportDefinitions",
        "cur:DeleteReportDefinition",
        "cur:PutReportDefinition",
        "events:CreateEventBus",
        "organizations:InviteAccountToOrganization",
        "s3:HeadBucket",
        "s3:HeadObject",
        "support:DescribeTrustedAdvisorCheckRefreshStatuses",
        "support:DescribeTrustedAdvisorCheckResult",
        "support:DescribeTrustedAdvisorChecks",
        "wellarchitected:*"
      ],
      "Effect": "Allow",
      "Resource": "*"
    },
    {
      "Action": [
        "acm-pca:Describe*",
        "acm-pca:Get*",
        "acm-pca:List*",
        "acm:Describe*",
        "acm:Get*",
        "acm:List*",
        "apigateway:GET",
        "appconfig:GetConfiguration*",
        "appflow:DescribeConnector*",
        "appflow:ListConnector*",
        "appstream:DescribeDirectoryConfigs",
        "appstream:DescribeUsers",
        "appstream:DescribeSessions",
        "appsync:Get*",
        "appsync:List*",
        "athena:Get*",
        "athena:List*",
        "backup:GetBackupVaultAccessPolicy",
        "cassandra:Select",
        "chime:Describe*",
        "chime:Get*",
        "chime:List*",
        "cloud9:Describe*",
        "cloud9:Get*",
        "cloud9:List*",
        "clouddirectory:Get*",
        "clouddirectory:List*",
        "cloudfront:GetCloudFrontOriginAccessIdentity",
        "cloudfront:GetFieldLevelEncryption*",
        "cloudfront:GetKeyGroupConfig",
        "cloudwatch:GetMetricData",
        "cloudwatch:GetMetricStream",
        "cloudwatch:ListMetricStreams",
        "codeartifact:GetAuthorizationToken",
        "codeartifact:ReadFromRepository",
        "codebuild:BatchGet*",
        "codebuild:ListSourceCredentials",
        "codecommit:BatchGet*",
        "codecommit:Get*",
        "codecommit:GitPull",
        "codedeploy:BatchGet*",
        "codedeploy:Get*",
        "codestar:DescribeUserProfile",
        "codestar:ListUserProfiles",
        "cognito-identity:*",
        "cognito-idp:*",
        "cognito-sync:*",
        "comprehend:Describe*",
        "comprehend:List*",
        "config:BatchGetAggregateResourceConfig",
        "config:BatchGetResourceConfig",
        "config:SelectAggregateResourceConfig",
        "config:SelectResourceConfig",
        "connect:Describe*",
        "connect:Get*",
        "connect:List*",
        "datapipeline:DescribeObjects",
        "datapipeline:EvaluateExpression",
        "datapipeline:QueryObjects",
        "dax:BatchGetItem",
        "dax:GetItem",
        "dax:Query",
        "deepcomposer:Get*",
        "deepcomposer:List*",
        "devicefarm:GetRemoteAccessSession",
        "devicefarm:ListRemoteAccessSessions",
        "directconnect:Describe*",
        "directconnect:List*",
        "discovery:Describe*",
        "discovery:Get*",
        "discovery:List*",
        "dms:Describe*",
        "dms:List*",
        "ds:Get*",
        "dynamodb:GetItem",
        "dynamodb:BatchGetItem",
        "dynamodb:Query",
        "dynamodb:Scan",
        "ec2:GetConsoleScreenshot",
        "ecr:BatchGetImage",
        "ecr:GetAuthorizationToken",
        "ecr:GetDownloadUrlForLayer",
        "ecr-public:GetAuthorizationToken",
        "eks:DescribeIdentityProviderConfig",
        "elasticbeanstalk:DescribeConfigurationOptions",
        "elasticbeanstalk:DescribeConfigurationSettings",
        "es:ESHttpGet*",
        "fis:GetExperimentTemplate",
        "fms:GetAdminAccount",
        "frauddetector:BatchGetVariable",
        "frauddetector:Get*",
        "gamelift:GetGameSessionLogUrl",
        "gamelift:GetInstanceAccess",
        "geo:ListDevicePositions",
        "glue:GetSecurityConfiguration*",
        "glue:SearchTables",
        "glue:GetTable*",
        "guardduty:GetIPSet",
        "guardduty:GetMasterAccount",
        "guardduty:GetMembers",
        "guardduty:ListMembers",
        "guardduty:ListOrganizationAdminAccounts",
        "inspector2:GetConfiguration",
        "imagebuilder:GetImage",
        "iotroborunner:Get*",
        "iotsitewise:ListAccessPolicies",
        "ivs:GetPlaybackKeyPair",
        "ivs:GetStreamSession",
        "kafka:GetBootstrapBrokers",
        "kendra:Query*",
        "kinesis:Get*",
        "kms:DescribeKey",
        "kms:GetPublicKey",
        "lex:Get*",
        "lambda:GetFunctionConfiguration",
        "license-manager:GetGrant",
        "license-manager:GetLicense",
        "license-manager:ListTokens",
        "lightsail:GetBucketAccessKeys",
        "lightsail:GetCertificates",
        "lightsail:GetContainerImages",
        "lightsail:GetKeyPair",
        "lightsail:GetRelationalDatabaseLogStreams",
        "logs:GetLogEvents",
        "logs:StartQuery",
        "machinelearning:GetMLModel",
        "macie2:GetAdministratorAccount",
        "macie2:GetMember",
        "macie2:GetMacieSession",
        "macie2:SearchResources",
        "macie2:GetSensitiveDataOccurrences",
        "mobilehub:ExportProject",
        "nimble:GetStreamingSession",
        "polly:SynthesizeSpeech",
        "proton:GetEnvironmentTemplate",
        "proton:GetServiceTemplate",
        "proton:ListServiceTemplates",
        "proton:ListEnvironmentTemplates",
        "qldb:GetBlock",
        "qldb:GetDigest",
        "rds:Download*",
        "rekognition:CompareFaces",
        "rekognition:Detect*",
        "rekognition:Search*",
        "resiliencehub:DescribeAppVersionTemplate",
        "resiliencehub:ListRecommendationTemplates",
        "robomaker:GetWorldTemplateBody",
        "s3-object-lambda:GetObject",
        "sagemaker:Search",
        "schemas:GetDiscoveredSchema",
        "sdb:Get*",
        "sdb:Select*",
        "secretsmanager:*",
        "securityhub:GetFindings",
        "securityhub:GetMembers",
        "securityhub:ListMembers",
        "ses:GetTemplate",
        "ses:GetEmailTemplate",
        "ses:GetContact",
        "ses:GetContactList",
        "ses:ListTemplates",
        "ses:ListEmailTemplates",
        "ses:ListVerifiedEmailAddresses",
        "signer:GetSigningProfile",
        "signer:ListProfilePermissions",
        "signer:ListSigningProfiles",
        "sms-voice:DescribeKeywords",
        "sms-voice:DescribeOptedOutNumbers",
        "sms-voice:DescribePhoneNumbers",
        "sms-voice:DescribePools",
        "snowball:Describe*",
        "sqs:Receive*",
        "ssm-contacts:*",
        "ssm:DescribeParameters*",
        "ssm:GetParameter*",
        "sso:Describe*",
        "sso:Get*",
        "sso:List*",
        "storagegateway:DescribeChapCredentials",
        "support:DescribeCommunications",
        "timestream:ListDatabases",
        "timestream:ListTables",
        "transcribe:Get*",
        "transcribe:List*",
        "transfer:Describe*",
        "transfer:List*",
        "waf-regional:GetChangeToken",
        "workmail:DescribeUser",
        "workmail:GetMailUserDetails",
        "workmail:ListUsers"
      ],
      "Effect": "Deny",
      "Resource": "*"
    }
  ]
}

 {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "s3:*"
            ],
            "Resource": [
                "arn:aws:s3:::[INSERT CUR S3 BUCKET]",
                "arn:aws:s3:::[INSERT CUR S3 BUCKET]/*"
            ],
            "Effect": "Allow"
        }
    ]
}

```

**Linked Account – IAM Policy JSON**
------------------------------------
```json
 {
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "support:DescribeTrustedAdvisorCheckRefreshStatuses",
        "support:DescribeTrustedAdvisorCheckResult",
        "support:DescribeTrustedAdvisorChecks",
        "wellarchitected:*"
      ],
      "Effect": "Allow",
      "Resource": "*"
    },
    {
      "Action": [
        "acm-pca:Describe*",
        "acm-pca:Get*",
        "acm-pca:List*",
        "acm:Describe*",
        "acm:Get*",
        "acm:List*",
        "apigateway:GET",
        "appconfig:GetConfiguration*",
        "appflow:DescribeConnector*",
        "appflow:ListConnector*",
        "appstream:DescribeDirectoryConfigs",
        "appstream:DescribeUsers",
        "appstream:DescribeSessions",
        "appsync:Get*",
        "appsync:List*",
        "athena:Get*",
        "athena:List*",
        "backup:GetBackupVaultAccessPolicy",
        "cassandra:Select",
        "chime:Describe*",
        "chime:Get*",
        "chime:List*",
        "cloud9:Describe*",
        "cloud9:Get*",
        "cloud9:List*",
        "clouddirectory:Get*",
        "clouddirectory:List*",
        "cloudfront:GetCloudFrontOriginAccessIdentity",
        "cloudfront:GetFieldLevelEncryption*",
        "cloudfront:GetKeyGroupConfig",
        "cloudwatch:GetMetricData",
        "cloudwatch:GetMetricStream",
        "cloudwatch:ListMetricStreams",
        "codeartifact:GetAuthorizationToken",
        "codeartifact:ReadFromRepository",
        "codebuild:BatchGet*",
        "codebuild:ListSourceCredentials",
        "codecommit:BatchGet*",
        "codecommit:Get*",
        "codecommit:GitPull",
        "codedeploy:BatchGet*",
        "codedeploy:Get*",
        "codestar:DescribeUserProfile",
        "codestar:ListUserProfiles",
        "cognito-identity:*",
        "cognito-idp:*",
        "cognito-sync:*",
        "comprehend:Describe*",
        "comprehend:List*",
        "config:BatchGetAggregateResourceConfig",
        "config:BatchGetResourceConfig",
        "config:SelectAggregateResourceConfig",
        "config:SelectResourceConfig",
        "connect:Describe*",
        "connect:Get*",
        "connect:List*",
        "datapipeline:DescribeObjects",
        "datapipeline:EvaluateExpression",
        "datapipeline:QueryObjects",
        "dax:BatchGetItem",
        "dax:GetItem",
        "dax:Query",
        "deepcomposer:Get*",
        "deepcomposer:List*",
        "devicefarm:GetRemoteAccessSession",
        "devicefarm:ListRemoteAccessSessions",
        "directconnect:Describe*",
        "directconnect:List*",
        "discovery:Describe*",
        "discovery:Get*",
        "discovery:List*",
        "dms:Describe*",
        "dms:List*",
        "ds:Get*",
        "dynamodb:GetItem",
        "dynamodb:BatchGetItem",
        "dynamodb:Query",
        "dynamodb:Scan",
        "ec2:GetConsoleScreenshot",
        "ecr:BatchGetImage",
        "ecr:GetAuthorizationToken",
        "ecr:GetDownloadUrlForLayer",
        "ecr-public:GetAuthorizationToken",
        "eks:DescribeIdentityProviderConfig",
        "elasticbeanstalk:DescribeConfigurationOptions",
        "elasticbeanstalk:DescribeConfigurationSettings",
        "es:ESHttpGet*",
        "fis:GetExperimentTemplate",
        "fms:GetAdminAccount",
        "frauddetector:BatchGetVariable",
        "frauddetector:Get*",
        "gamelift:GetGameSessionLogUrl",
        "gamelift:GetInstanceAccess",
        "geo:ListDevicePositions",
        "glue:GetSecurityConfiguration*",
        "glue:SearchTables",
        "glue:GetTable*",
        "guardduty:GetIPSet",
        "guardduty:GetMasterAccount",
        "guardduty:GetMembers",
        "guardduty:ListMembers",
        "guardduty:ListOrganizationAdminAccounts",
        "inspector2:GetConfiguration",
        "imagebuilder:GetImage",
        "iotroborunner:Get*",
        "iotsitewise:ListAccessPolicies",
        "ivs:GetPlaybackKeyPair",
        "ivs:GetStreamSession",
        "kafka:GetBootstrapBrokers",
        "kendra:Query*",
        "kinesis:Get*",
        "kms:DescribeKey",
        "kms:GetPublicKey",
        "lex:Get*",
        "lambda:GetFunctionConfiguration",
        "license-manager:GetGrant",
        "license-manager:GetLicense",
        "license-manager:ListTokens",
        "lightsail:GetBucketAccessKeys",
        "lightsail:GetCertificates",
        "lightsail:GetContainerImages",
        "lightsail:GetKeyPair",
        "lightsail:GetRelationalDatabaseLogStreams",
        "logs:GetLogEvents",
        "logs:StartQuery",
        "machinelearning:GetMLModel",
        "macie2:GetAdministratorAccount",
        "macie2:GetMember",
        "macie2:GetMacieSession",
        "macie2:SearchResources",
        "macie2:GetSensitiveDataOccurrences",
        "mobilehub:ExportProject",
        "nimble:GetStreamingSession",
        "polly:SynthesizeSpeech",
        "proton:GetEnvironmentTemplate",
        "proton:GetServiceTemplate",
        "proton:ListServiceTemplates",
        "proton:ListEnvironmentTemplates",
        "qldb:GetBlock",
        "qldb:GetDigest",
        "rds:Download*",
        "rekognition:CompareFaces",
        "rekognition:Detect*",
        "rekognition:Search*",
        "resiliencehub:DescribeAppVersionTemplate",
        "resiliencehub:ListRecommendationTemplates",
        "robomaker:GetWorldTemplateBody",
        "s3-object-lambda:GetObject",
        "sagemaker:Search",
        "schemas:GetDiscoveredSchema",
        "sdb:Get*",
        "sdb:Select*",
        "secretsmanager:*",
        "securityhub:GetFindings",
        "securityhub:GetMembers",
        "securityhub:ListMembers",
        "ses:GetTemplate",
        "ses:GetEmailTemplate",
        "ses:GetContact",
        "ses:GetContactList",
        "ses:ListTemplates",
        "ses:ListEmailTemplates",
        "ses:ListVerifiedEmailAddresses",
        "signer:GetSigningProfile",
        "signer:ListProfilePermissions",
        "signer:ListSigningProfiles",
        "sms-voice:DescribeKeywords",
        "sms-voice:DescribeOptedOutNumbers",
        "sms-voice:DescribePhoneNumbers",
        "sms-voice:DescribePools",
        "snowball:Describe*",
        "sqs:Receive*",
        "ssm-contacts:*",
        "ssm:DescribeParameters*",
        "ssm:GetParameter*",
        "sso:Describe*",
        "sso:Get*",
        "sso:List*",
        "storagegateway:DescribeChapCredentials",
        "support:DescribeCommunications",
        "timestream:ListDatabases",
        "timestream:ListTables",
        "transcribe:Get*",
        "transcribe:List*",
        "transfer:Describe*",
        "transfer:List*",
        "waf-regional:GetChangeToken",
        "workmail:DescribeUser",
        "workmail:GetMailUserDetails",
        "workmail:ListUsers"
      ],
      "Effect": "Deny",
      "Resource": "*"
    }
  ]
}

```