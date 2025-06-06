# AMI

- AMI: Amazon Machine Image
- AMI are a **customization** of an EC2 instance
    - You add your own software, configuration, operating system, monitoring etc
    - Faster boot / configuration time because all your software is pre-packaged
- AMI are built for a specific region (and can be copied across regions)
- You can launch EC2 instances from
    - A Public AMI: AWS provided
    - Your own AMI: you make and maintain them yourself
    - An AWS Marketplace AMI: an AMI someone else made (and potentially sells)

### AMI Process (from an EC2 instance)
- Start an EC2 instance
- Stop the instance (for data integrity)
- Build an AMI - this will also create EBS snapshots
- Launch instances from other AMIs

<br><br>

![AMI-example](/3%20-%20EBS/images/2-AMI-process.svg)