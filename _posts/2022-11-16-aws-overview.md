---
title: AWS Overview
categories:
- aws
date: '2022-11-16 00:00:00'
image: assets/images/blog/2022/11/16/aws-regions.jpg
---

### AWS Regions
* AWS has Regions all around the world
* Names can be us-east-1, eu-west-3…
* A region is a cluster of data centers
* Most AWS services are region-scoped

### How to choose an AWS Region?
* Compliance with data governance and legal
requirements: data never leaves a region without
your explicit permission
* Proximity to customers: reduced latency
* Available services within a Region: new services
and new features aren’t available in every Region
* Pricing: pricing varies region to region and is
transparent in the service pricing page

### AWS Availability Zones
* Each region has many availability zones
(usually 3, min is 2, max is 6). Example:
    * ap-southeast-2a
    * ap-southeast-2b
    * ap-southeast-2c
		
* Each availability zone (AZ) is one or more
discrete data centers with redundant power,
networking, and connectivity
* They’re separate from each other, so that
they’re isolated from disasters
* They’re connected with high bandwidth,
ultra-low latency networking

### Tour of the AWS Console
* AWS has Global Services:
    * Identity and Access Management (IAM)
    * Route 53 (DNS service)
    * CloudFront (Content Delivery Network)
    * WAF (Web Application Firewall)

* Most AWS services are Region-scoped:
    * Amazon EC2 (Infrastructure as a Service)
    * Elastic Beanstalk (Platform as a Service)
    * Lambda (Function as a Service)
    * Rekognition (Software as a Service)
