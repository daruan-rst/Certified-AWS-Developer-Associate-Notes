# EBS Introduction

## What is an EBS Volume?
 - An EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run
 - It allows your instances to persist datra even after their termination
 - **They can only be mounted to one instance at a time (at the CCP level¹)**
 - They are bound to a specific availability zone
 <br><br>
 - Analogy : Think of thhem as a "network USB stick" 
 <br><br>
 - Free tier: 30GB of free EBS Storage of type General Purpose (SSD) or magnetic per month
 

 ## EBS Volume
  - It's a network drive (i.e. not a physical drive)
    - It uses the network to communicate the instance, which means there might be a bit of latency
    - It can be detached from and EC2 instance and attched to another one quickly
<br><br>
- Its locked to an Availabillity Zone (AZ)
    - An EBS Volume in us-east-1a cannot be attached to us-east-1b
    - To move a volume across, you first need to snapshot it
<br><br>
- Have a provisioned capacity (size in GBs and IOPS)
    = You get billed for all the provisioned capacity

### EBS Example


![EbsVolume-example](/3%20-%20EBS/images/1-EbsVolume-example.svg)


___

¹ CCP - Certified Cloud Practitioner - one EBS can be only mounted to one EC2 instance Associate LEvel (Solutions Architect, Developer, SysOps): "multi-attach" for some EBS.