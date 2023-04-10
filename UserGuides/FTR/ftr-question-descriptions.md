---
title: FTR Question Descriptions
parent: FTR
grand_parent: User Guides
nav_order: 2
layout: default
---

{: .no_toc }
# FTR Question Descriptions #
=============================

The Foundational Technical Review (FTR) Lens provides a set of specific questions for independent software vendors (ISVs) to perform a workload assessment. To understand what the question is asking, below is a definition of each question in the FTR.

{: .no_toc }
## List of Questions and the descriptions: ##
===========================================


- TOC
{:toc}

### 1\. Support Level ###

**Enable AWS Business Support (or greater) on all production AWS accounts.**

_AWS Support provides a mix of tools and technology, people, and programs designed to proactively help you optimize performance, lower costs, and innovate faster. AWS Business Support provides additional benefits including access to AWS Trusted Advisor and AWS Personal Health Dashboard and faster response times. Subscribing to AWS Business Support or greater for all production accounts is a requirement to successfully complete the FTR. Business Support billing calculations are performed on a per-account basis. Monthly charges are based on each month's AWS usage charges, subject to monthly minimum. For latest pricing information see Premium Support Pricing._

### 2\. AWS Well-Architected Review ###

**Conduct a Well-Architected Review with FTR Lens on the production workload on a periodic basis(minimum once every year).**

_The AWS Well-Architected Tool helps you review the state of your workloads and compares them to the latest AWS architectural best practices. The tool is based on the AWS Well-Architected Framework, developed to help cloud architects build secure, high-performing, resilient, and efficient application infrastructure. Well Architected Reviews must be conducted on the production workload on a periodic basis. After conducting the review, you should prioritize the remediation of any identified issues according to your business priorities. It is not a requirement to complete the remediation of any issues identified in the review other than the requirements defined in this checklist._

### 3\. AWS Root Account ###

**Use root user is only by exception.**

  
_The root user has unlimited access to your account and its resources, and using it only by exception helps protect your AWS resources. The AWS root user must not be used for everyday tasks, even administrative ones. Instead, adhere to the best practice of using the root user only to create your first AWS Identity and Access Management (IAM) user. Then securely lock away the root user credentials and use them to perform only a few account and service management tasks. To view the tasks that require you to sign in as the root user, see AWS Tasks That Require Root User. To learn more about FTR AWS root account protection and IAM configuration requirements, watch Baseline Bits: 03 AWS Root Account Protection and AWS Identity and Access Management Configuration._

**Remove access keys for the root user.**

_Programmatic access to AWS APIs should never use the root user. It is best not to generate a static access key for the root user. If one already exists, you should transition any processes using that key to use temporary access keys from an AWS Identity and Access Management (IAM) role, or, if necessary, static access keys from an IAM user._

**Enable multi-factor authentication (MFA) on root user.**

_If an account is not managed by AWS Organizations, enabling MFA provides an additional control for account sign-in. Because your root user can perform sensitive operations in your account, adding an additional layer of authentication helps you to better secure your account. Multiple types of MFA are available, including virtual MFA and hardware MFA. To learn more about FTR AWS root account protection and AWS Identity and Access Management configuration requirements, watch Baseline Bits: 03 AWS Root Account Protection and AWS Identity and Access Management Configuration._

**Create an incident response (IR) runbook for root account credential misuse.**

_A runbook that details an appropriate response to root account credential misuse enables you to promptly act in the event that your root user becomes compromised. In the event your root account credentials are inaccessible, you will need to either change your AWS account root user password, or contact account and billing support through the Unable to Sign in & Submit Billing or Account Request page._

### 4\. AWS accounts ###

**Use separate accounts for production and non-production stages.**

_Multiple AWS accounts allow you to separate data and resources, and enable the use of Service Control Policies to implement guardrails. For example, users outside of your account do not have access to your resources by default. Similarly, the cost of AWS resources that you consume is allocated to your account. AWS recommends that you use multiple AWS Accounts to separate workloads and workload stages, such as production and non-production._

### 5\. Communications from AWS ###


**Configure AWS account contacts.**

_If an account is not managed by AWS Organizations , alternate account contacts help AWS get in contact with the appropriate personnel if needed. Configure the account’s alternate contacts to point to a group rather than an individual. For example, create separate email distribution lists for billing, operations, and security and configure these as Billing, Security, and Operations contacts in each active AWS account. This ensures that multiple people will receive AWS notifications and be able to respond, even if someone is on vacation, changes roles, or leaves the company._

**Set account contact information including the root user email address to email addresses and phone numbers owned by your company.**

_Using company-owned email addresses and phone numbers for contact information enables you to access them even if the individuals whom they belong to are no longer with your organization._

### 6\. CloudTrail ###


**Configure CloudTrail in all AWS Accounts and in all Regions**.

_AWS CloudTrail enables governance, compliance, operational auditing, and risk auditing of your AWS account. To meet FTR requirements, you must have management events enabled for all AWS accounts and aggregate these logs into an Amazon Simple Storage Service (Amazon S3) bucket owned by a separate AWS account. The first copy of management events in each region is delivered free of charge and you only pay for S3 storage cost. Additional copies of management events will incur charges. Should you enable data events, you will incur charges for each copy along with associated S3 storage costs. For the latest pricing information see CloudTrail pricing. To learn more about FTR audit and logging requirements, watch Baseline Bits 05: Audit and Logging on AWS Accounts._

**Store logs in a separate administrative domain with limited access (e.g. Separate AWS Account or an equivalent AWS Partner solution).**

_Configuring the logs to flow to a central account (i.e. separate AWS Account that is only intended for log storage and limited access ) or an equivalent AWS Partner solution protects the logs from manipulation or deletion. To learn more about FTR audit and logging requirements, watch Baseline Bits 05: Audit and Logging on AWS Accounts._

**Protect log storage from unintended access (e.g. MFA-delete, versioning on S3, object lock, or an equivalent solution)**

_Protecting log storage locations from unintended access helps with avoiding any unintended changes to log files._

**Enable CloudTrail log file integrity validation.**

_A validated log file using integrity validation enables you to assert positively that the log file itself has not changed, or that particular user credentials performed specific API activity. The CloudTrail log file integrity validation process also lets you know if a log file has been deleted or changed, or assert positively that no log files were delivered to your account during a given period of time. CloudTrail log file integrity validation uses industry-standard algorithms: SHA-256 for hashing and SHA-256 with RSA for digital signing. This makes it computationally unfeasible to modify, delete or forge CloudTrail log files without detection. For more information, see Enabling Validation and Validating Files._

### 7\. Identity and Access Management ###


**Enable multi-factor authentication for all Human Identities with AWS access.**

_You must require any human identities to authenticate using MFA before accessing your AWS accounts. Typically this means enabling MFA within your corporate identity provider. If you have existing legacy IAM users you must enable MFA for console access for those principals as well. Enabling MFA for IAM users provides an additional layer of security. With MFA, users have a device that generates a unique authentication code (a one-time password, or OTP). Users must provide both their normal credentials (user name and password) and the OTP. The MFA device can either be a special piece of hardware, or it can be a virtual device (for example, it can run in an app on a smartphone). To learn more about FTR IAM configuration requirements, watch Baseline Bits: 03 AWS Root Account Protection and AWS Identity and Access Management Configuration. Please note that Machine Identities do not require MFA._

**Rotate credentials regularly.**

_When you cannot rely on temporary credentials and require long term credentials, rotate the IAM access keys regularly. If an access key is compromised without your knowledge, you limit how long the credentials can be used to access your resources. For information about rotating access keys for IAM users, see Rotating Access Keys. To learn more about FTR IAM configuration requirements, watch Baseline Bits: 03 AWS Root Account Protection and AWS Identity and Access Management Configuration._

**Use strong password policy.**

_Enforce a strong password policy, and educate users to avoid common or re-used passwords. For IAM users, you can create a password policy for your account on the Account Settings page of the IAM console. You can use the password policy to define password requirements, such as minimum length, whether it requires non-alphabetic characters, and so on. For more information, see Setting an Account Password Policy for IAM Users. To learn more about FTR IAM configuration requirements, watch Baseline Bits: 03 AWS Root Account Protection and AWS Identity and Access Management Configuration._

**Create individual identities (no shared credentials) for anyone who needs AWS access.**

_By creating individual identities for people accessing your account, you can give each user a unique set of security credentials and permissions. Individual users provide the ability to audit each users activity. To learn more about FTR IAM configuration requirements, watch Baseline Bits: 03 AWS Root Account Protection and AWS Identity and Access Management Configuration._

**Use IAM roles and its temporary security credentials to provide access to third parties.**

_Do not provision IAM users and share those credentials with people outside of your organization. Any external services that need to make AWS API calls against your account (e.g. a monitoring solution that accesses your account's AWS CloudWatch metrics) must use a cross-account role. See documentation on providing access to AWS accounts owned by third parties for more information._

**Grant least privilege access.**

_You must follow the standard security advice of granting the least privilege. Grant only the access that identities require by allowing access to specific actions on specific AWS resources under specific conditions. Rely on groups and identity attributes to dynamically set permissions at scale, rather than defining permissions for individual users. For example, you can allow a group of developers access to manage only resources for their project. This way, when a developer is removed from the group, access for the developer is revoked everywhere that group was used for access control, without requiring any changes to the access policies. To learn more about FTR IAM configuration requirements, watch Baseline Bits: 03 AWS Root Account Protection and AWS Identity and Access Management Configuration._

**Manage access based on life cycle.**

_Integrate access controls with operator and application lifecycle and your centralized federation provider and IAM. For example, remove a user’s access when they leave the organization or change roles_

**Audit identities quarterly.**

_Auditing the identities that are configured in your identity provider and IAM helps ensure that only authorized identities have access to your workload. For example, remove people that leave the organization, and remove cross-account roles that are no longer required. Have a process in place to periodically audit permissions to the services accessed by an IAM entity. This helps you identify the policies you need to modify to remove any unused permissions, see IAM access advisor._

**Do not embed credentials in application code.**

_Ensure all credentials used by your applications (e.g. IAM access keys, database passwords, etc.) are never included in your application's source code or committed to source control in any way._

**Store secrets in specialized service.**

_Where you cannot use temporary credentials, such as tokens from AWS Security Token Service, storing your secrets, such as database passwords, using a service like AWS Secrets Manager or an equivalent AWS Partner solution, helps secure your credentials._

**Encrypt all end user/customer credentials and hash passwords at rest.**

_If storing end user/customer credentials in a database that you manage, encrypt credentials at rest and hash passwords. As an alternative, AWS recommends using a user identity synchronization service, such as Amazon Cognito or an equivalent AWS Partner solution._

### 8\. Backups and Recovery ###


**Perform data backup automatically.**

_You must perform regular backups to a durable storage service. Backups ensure that you have the ability to recover from administrative, logical, or physical error scenarios. Configure backups to be taken automatically based on a periodic schedule, or by changes in the dataset. RDS instances, EBS volumes, DynamoDB tables, and S3 objects can all be configured for automatic backup. AWS Marketplace solutions or third-party solutions can also be used. To learn more about FTR backup and recovery requirements, watch Baseline Bits 07: Backups and Disaster Recovery._

**Perform periodic recovery of the data to verify backup integrity and processes.**

_Validate that your backup process implementation meets your recovery time objectives (RTO) and recovery point objectives (RPO) by performing a recovery test both on a periodic basis and after making significant changes to your cloud environment. AWS provides resources to help you manage backup and restore of your data. To learn more about FTR backup and recovery requirements, watch Baseline Bits 07: Backups and Disaster Recovery._

### 9\. Disaster Recovery ###


**Define a Recovery Point Objective (RPO) according to your organizational needs.**

_Your data loss tolerance is the basis of your backup strategy and frequency. Recovery Point Objective (RPO) defines your data loss tolerance in-terms of time. Define a Recovery Point Objective (RPO) according to your organizational needs._

**Establish a Recovery Time Objective (RTO) to meet business needs and expectations. This should be on the order of minutes for all components that are critical for providing service to your customers but should never exceed 24 hours.**

_Recovery Time Objective (RTO) defines your tolerance for downtime. The FTR requirement is for the RTO to be less than 24._

**Test disaster recovery implementation to validate the implementation.**

_Test failover to DR to ensure that RTO and RPO are met, both periodically and after major updates. The DR test must include accidental data loss, instance, and Availability Zone (AZ) failures. At least one DR test that passes RTO and RPO requirements must be completed prior to FTR approval._

### 10\. Amazon S3 Bucket Access ###


**Review all Amazon S3 buckets to determine appropriate access levels.**

_You must ensure that buckets that require public access have been reviewed to determine if public read or write access is needed, and appropriate controls are in place to control public access. When using AWS, it's best practice to restrict access to your resources to the people that absolutely need it (the principle of least privilege). To learn more about FTR S3 bucket access management requirements, watch Baseline Bits 06: S3 Bucket Access Management and Configuration._

  
**Restrict access to S3 buckets that should not have public access.**

_You must ensure that buckets that should not allow public access are properly configured to prevent public access. By default, all S3 buckets are private, and can only be accessed by users that have been explicitly granted access. Most use cases won't require broad-ranging public access to read files from your S3 buckets, unless you're using S3 to host public assets (for example, to host images for use on a public website), and it's best practice to never open access to the public. To learn more about FTR S3 bucket access management requirements, watch Baseline Bits 06: S3 Bucket Access Management and Configuration.  
_

**Implement monitoring and alerting to identify when S3 buckets become public.**

_You must have monitoring or alerting in place to identify when S3 buckets become public. Trusted Advisor checks for S3 buckets that have open access permissions. Bucket permissions that grant List access to everyone can result in higher than expected charges if objects in the bucket are listed by unintended users at a high frequency. Bucket permissions that grant Upload/Delete access to everyone create potential security vulnerabilities by allowing anyone to add, modify, or remove items in a bucket. The Trusted Advisor check examines explicit bucket permissions and associated bucket policies that might override the bucket permissions. You can also use AWS Config to monitor your S3 buckets for public access. For more information on using AWS Config to monitor S3, please take a look at this blog. To learn more about FTR S3 bucket access management requirements, watch Baseline Bits 06: S3 Bucket Access Management and Configuration._

### 11\. Cross-Account Access ###


**Use cross-account roles to access customer accounts.**

_Cross-account roles reduce the amount of sensitive information AWS Partners need to store for their customers. To learn more about FTR cross-account access requirements, watch Baseline Bits 04: Using AWS Identity and Access Management Roles for Cross-Account Access._

**Provide guidance or an automated setup mechanism (e.g. AWS CloudFormation template) for creating cross-account role with minimum required privileges.**

_The policy created for cross-account access in customer accounts must follow the least privilege principle. The partner must provide a role policy document or an automated setup mechanism (e.g. an AWS CloudFormation template) for the customers to use to ensure that the roles are created with minimum required privileges._

**Use external ID with cross-account roles to access customer accounts.**

_The external ID allows the user that is assuming the role to assert the circumstances in which they are operating. It also provides a way for the account owner to permit the role to be assumed only under specific circumstances. The primary function of the external ID is to address and prevent the confused deputy problem._

**Use a value you generate (not something provided by the customer) for the external ID.**

_When configuring cross-account access using IAM roles, you must use a value you generate for the external ID, instead of one provided by the customer, to ensure the integrity of the cross account role configuration. A partner-generated external ID ensures that malicious parties cannot impersonate a customer's configuration and enforces uniqueness and format consistency across all customers. If you are not generating an external ID today we recommend implementing a process that ensures a random unique value, such as a Universally Unique Identifier, is generated for the external ID that a customer would use to setup a cross account role._

**Ensure all external IDs are unique.**  

_The external IDs used must be unique across all customers. Re-using external IDs for different customers does not solve the confused deputy problem and runs the risk of customer A being able to view data of customer B by using the role ARN of customer B along with the external ID of customer B. To resolve this, we recommend implementing a process that ensures a random unique value, such as a Universally Unique Identifier, is generated for the external ID that a customer would use to setup a cross account role._

**Provide read-only access to external ID to customers.**

_Customers must not be able to set or influence external IDs. When the external ID is editable, it is possible for one customer to impersonate the configuration of another. When the external ID is editable Customer A can create a cross account role setup using customer B’s role ARN and external id, granting customer A access to customer B’s data. Remediation of this item involves making the external ID a view only field ensuring that the external ID cannot be changed for purposes of impersonating the setup of another customer._

**Deprecate any historical use of customer-provided IAM credentials.**

_If your application provides legacy support for the use of static IAM credentials for cross-account access, the application's user interface and customer documentation must make it clear that this method is deprecated and the use of a cross-account IAM role is recommended. Existing customers should be encouraged to switch to cross-account role based-access, and collection of credentials should be disabled for new customers. To learn more about FTR cross-account access requirements, watch Baseline Bits 04: Using AWS Identity and Access Management Roles for Cross-Account Access_

### 12\. Sensitive Data ###


**Identify sensitive data (e.g. Personally Identifiable Information (PII) and Protected Health Information (PHI)).**

_Data classification enables you to determine which data needs to be protected and how. Based on the workload and the data it processes, identify the data that is not common public knowledge._

**Encrypt all sensitive data at rest.**

_Encryption maintains the confidentiality of sensitive data even when it gets stolen or the network through which it is transmitted becomes compromised._

**Only use protocols with encryption when transmitting sensitive data.**

_Encryption maintains data confidentiality even when the network through which it is transmitted becomes compromised._

**Log access to sensitive data comprehensively throughout the system**

_Visibility into any unexpected access to sensitive data provides you with the opportunity to perform necessary corrective actions to further protect your data. Scope your systems for components that store sensitive data. Implement application- and resource-level auditing and logging to monitor all access to data and quickly identify unauthorized access._

### 13\. Protected Health Information ###


**If the solution handles Protected Health Information (PHI), the partner must have a Business Associate Addendum (BAA) in place with AWS for every AWS account with PHI**

_Have a Business Associate Addendum (BAA) in place with AWS for every AWS account with Protected Health Information (PHI)._

**Only use services in the HIPAA Eligible Services Reference for solutions that handle PHI.**

_Solutions handling PHI must use services in the HIPAA Eligible Services Reference._

### 14\. Regulatory Compliance Validation Process ###


**Establish a process to ensure that all required compliance standards are met.**

_If you advertise that your product meets specific compliance standards, you must have an internal process for ensuring compliance. Examples of compliance standards include PCI DSS, FedRAMP, and HIPAA. Applicable compliance standards are determined by various factors, such as what types of data the solution stores or transmits and which geographic regions the solution supports._