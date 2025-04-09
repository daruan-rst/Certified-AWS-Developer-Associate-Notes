# EC2

- EC2 = Elastic Compute Cloud
    - Infrastructure as a Service

- It mainly consists of: 
    - Renting virtual machines (EC2)
    - Storing data on Virtual Drives (EBS)
    - Distribute Load Across machines (ELB)
    - Scale the services using an auto-scaling group (ASG)
- Knowing EC2 is fundamental to understand how the cloud works

### EC2 Sizing and configuration options

- Operating System (OS): Linux, Windows or Mac OS
- How much compute power and cores (CPU)
- Hom much random-access memory (RAM)
- How much storage space: 
    - Network-attached (EBS & EFS)
    - Hardware-attached (EC2 instance store)
- Network card: speed of the card, public IP address
- Firewall rules: security group
- Bootstrap script to configure the instance at first launch: EC2 User Data

### EC2 User Data

- It is possible to bootstrap our instances using an EC2 User Data Script
- Bootstraping means launching commands when a machine starts 
- That script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as:
    - Installing updates
    - Installing software
    - Downloading common files from the internet 
    