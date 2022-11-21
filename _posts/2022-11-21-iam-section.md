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
