---
title: IAM Section
categories:
- aws
date: '2022-11-21 14:29:00'
image: assets/images/blog/2022/11/16/aws-regions.jpg
---

### IAM: Users & Groups
* IAM = Identity and Access Management, Global service
* Root account created by default, shouldn’t be used or shared
*  Users are people within your organization, and can be grouped
*  Groups only contain users, not other groups
*  Users don’t have to belong to a group, and user can belong to multiple groups

![]({{ 'assets/images/blog/2022/11/21/user-group.jpg' | relative_url }})

### IAM: Permissions
* Users or Groups can be
assigned JSON documents
called policies
* These policies define the
permissions of the users
* In AWS you apply the least
privilege principle: don’t give
more permissions than a user
needs 
![]({{ 'assets/images/blog/2022/11/21/policies.jpg' | relative_url }})

### IAM Policies inheritance
![]({{ 'assets/images/blog/2022/11/21/inheritance.jpg' | relative_url }})

### IAM Policies Structure
* Consists of
    * Version: policy language version, always include “2012-10-17”
    * Id: an identifier for the policy (optional)
    * Statement: one or more individual statements (required)

* Statements consists of
    * Sid: an identifier for the statement (optional)
    * Effect: whether the statement allows or denies access (Allow, Deny)
    * Principal: account/user/role to which this policy applied to
    * Action: list of actions this policy allows or denies
    * Resource: list of resources to which the actions applied to
    * Condition: conditions for when this policy is in effect (optional)

![]({{ 'assets/images/blog/2022/11/21/policies_struct.jpg' | relative_url }})

### IAM – Password Policy
* Strong passwords = higher security for your account
* In AWS, you can setup a password policy:
    * Set a minimum password length
    * Require specific character types:
        * including uppercase letters
        * lowercase letters
        * numbers
        * non-alphanumeric characters
     * Allow all IAM users to change their own passwords
     * Require users to change their password after some time (password expiration)
     * Prevent password re-use

### Multi Factor Authentication - MFA
* Users have access to your account and can possibly change configurations or delete resources in your AWS account
* You want to protect your Root Accounts and IAM users
* MFA = password you know + security device you own
![]({{ 'assets/images/blog/2022/11/21/MFA.jpg' | relative_url }})
* Main benefit of MFA: if a password is stolen or hacked, the account is not compromised

### MFA devices options in AWS
* Virtual MFA device
* Universal 2nd Factor (U2F) Security Key
* Hardware Key Fob MFA Device 
* Hardware Key Fob MFA Device for AWS GovCloud (US)

### How can users access AWS ?
* To access AWS, you have three options:
    * AWS Management Console (protected by password + MFA)
    * AWS Command Line Interface (CLI): protected by access keys
    * AWS Software Developer Kit (SDK) - for code: protected by access keys

* Access Keys are generated through the AWS Console
* Users manage their own access keys
* **Access Keys are secret, just like a password. Don’t share them**
* Access Key ID ~= username
* Secret Access Key ~= password

### What’s the AWS CLI?
* A tool that enables you to interact with AWS services using commands in your command-line shell
* It’s open-source https://github.com/aws/aws-cli
* Direct access to the public APIs of AWS services

### What’s the AWS SDK?
* AWS Software Development Kit (AWS SDK)
* Language-specific APIs (set of libraries)
* Enables you to access and manage AWS services programmatically

### IAM Roles for Services
* Some AWS service will need to perform actions on your behalf
* To do so, we will assign permissions to AWS services with IAM Roles
* Common roles:
    * EC2 Instance Roles
    * Lambda Function Roles
    * Roles for CloudFormation

### IAM Security Tools
* IAM Credentials Report (account-level)
    * a report that lists all your account's users and the status of their various credentials
    
* IAM Access Advisor (user-level)
    * Access advisor shows the service permissions granted to a user and when those services were last accessed.
    * You can use this information to revise your policies.
    
### IAM Guidelines & Best Practices
* Don’t use the root account except for AWS account setup
* One physical user = One AWS user
* Assign users to groups and assign permissions to groups
* Create a strong password policy
* Use and enforce the use of Multi Factor Authentication (MFA)
* Create and use Roles for giving permissions to AWS services
* Use Access Keys for Programmatic Access (CLI / SDK)
* Audit permissions of your account with the IAM Credentials Report
* Never share IAM users & Access Keys

### IAM Section – Summary
* **Users:** mapped to a physical user, has a password for AWS Console
* **Groups:** contains users only
* **Policies:** JSON document that outlines permissions for users or groups
* **Roles:** for EC2 instances or AWS services
* **Security:** MFA + Password Policy
* **Access Keys:**  access AWS using the CLI or SDK
* **Audit:** IAM Credential Reports & IAM Access Advisor
