---
title: EC2 Instance Storage Section
categories:
- aws
date: '2022-11-24 16:15:23'
image: assets/images/blog/2022/11/16/aws-regions.jpg
---

### What’s an EBS Volume?
* An EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run
* It allows your instances to persist data, even after their termination
* **They can only be mounted to one instance at a time** (at the CCP level)
* They are bound to **a specific availability zone**
* Analogy: Think of them as a “network USB stick”
* Free tier: 30 GB of free EBS storage of type General Purpose (SSD) or Magnetic per month
