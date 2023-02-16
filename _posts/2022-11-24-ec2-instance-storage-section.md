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

### EBS Volume
* It’s a network drive (i.e. not a physical drive)
    * It uses the network to communicate the instance, which means there might be a bit of latency
    * It can be detached from an EC2 instance and attached to another one quickly

* It’s locked to an Availability Zone (AZ)
    * An EBS Volume in us-east-1a cannot be attached to us-east-1b
    * To move a volume across, you first need to snapshot it

* Have a provisioned capacity (size in GBs, and IOPS)
    * You get billed for all the provisioned capacity
    * You can increase the capacity of the drive over time

### EBS Volume - Example
![]({{ 'assets/images/blog/2022/11/21/EBSVolume.jpg' | relative_url }})

### EBS – Delete on Termination attribute
![]({{ 'assets/images/blog/2022/11/21/EBSDeleteAttr.jpg' | relative_url }})

* Controls the EBS behaviour when an EC2 instance terminates
    * By default, the root EBS volume is deleted (attribute enabled)
    * By default, any other attached EBS volume is not deleted (attribute disabled)

* This can be controlled by the AWS console / AWS CLI
* **Use case: preserve root volume when instance is terminated**

### EBS Snapshots
* Make a backup (snapshot) of your EBS volume at a point in time
* Not necessary to detach volume to do snapshot, but recommended
* Can copy snapshots across AZ or Region

![]({{ 'assets/images/blog/2022/11/21/SnapshotEBS.jpg' | relative_url }})

### EBS Snapshots Features
* EBS Snapshot Archive
    * Move a Snapshot to an ”archive tier” that is 75% cheaper
    * Takes within 24 to 72 hours for restoring the archive

* Recycle Bin for EBS Snapshots
    * Setup rules to retain deleted snapshots so you can recover them after an accidental deletion
    * Specify retention (from 1 day to 1 year)

* Fast Snapshot Restore (FSR)
    * Force full initialization of snapshot to have no latency on the first use ($$$)

![]({{ 'assets/images/blog/2022/11/21/EBSSnapshotFeature.jpg' | relative_url }})

### AMI Overview
* AMI = Amazon Machine Image
* AMI are a **customization** of an EC2 instance
    * You add your own software, configuration, operating system, monitoring…
    * Faster boot / configuration time because all your software is pre-packaged

* AMI are built for a **specific region** (and can be copied across regions)
* You can launch EC2 instances from:
    * **A Public AMI:** AWS provided
    * **Your own AMI:** you make and maintain them yourself
    * **An AWS Marketplace AMI:** an AMI someone else made (and potentially sells)

### AMI Process (from an EC2 instance)
* Start an EC2 instance and customize it
* Stop the instance (for data integrity)
* Build an AMI – this will also create EBS snapshots
* Launch instances from other AMIs

![]({{ 'assets/images/blog/2022/11/21/CustomAMI.jpg' | relative_url }})

### EC2 Instance Store
* EBS volumes are network drives with good but “limited” performance
* **If you need a high-performance hardware disk, use EC2 Instance Store**
* Better I/O performance
* EC2 Instance Store lose their storage if they’re stopped (ephemeral)
* Good for buffer / cache / scratch data / temporary content
* Risk of data loss if hardware fails
* Backups and Replication are your responsibility 

![]({{ 'assets/images/blog/2022/11/21/InstanceStore.jpg' | relative_url }})

### EBS Volume Types
* EBS Volumes come in 6 types
    * **gp2 / gp3 (SSD):** General purpose SSD volume that balances price and performance for a wide variety of workloads
    * **io1 / io2 (SSD):** Highest-performance SSD volume for mission-critical low-latency or high-throughput workloads
    * **st1 (HDD):** Low cost HDD volume designed for frequently accessed, throughput- intensive workloads
    * **sc1 (HDD):** Lowest cost HDD volume designed for less frequently accessed workloads

* EBS Volumes are characterized in Size | Throughput | IOPS (I/O Ops Per Sec)
* When in doubt always consult the AWS documentation – it’s good!
* **Only gp2/gp3 and io1/io2 can be used as boot volumes**

### EBS Volume Types Use cases - General Purpose SSD
* Cost effective storage, low-latency
* System boot volumes, Virtual desktops, Development and test environments
* 1 GiB - 16 TiB
* gp3:
    * Baseline of 3,000 IOPS and throughput of 125 MiB/s
    * Can increase IOPS up to 16,000 and throughput up to 1000 MiB/s independently

* gp2:
    * Small gp2 volumes can burst IOPS to 3,000
    * Size of the volume and IOPS are linked, max IOPS is 16,000
    * 3 IOPS per GB, means at 5,334 GB we are at the max IOPS
