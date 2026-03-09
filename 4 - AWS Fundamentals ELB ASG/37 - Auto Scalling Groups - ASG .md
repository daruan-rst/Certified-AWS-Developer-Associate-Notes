# Auto Scalling Groups (ASG)

## What is an Auto scalling group?

- In real-life, the load on your websites and application can change
- In the cloud, you can create and get rid of servers very quickly
- The goal of an Auto Scaling Group (ASG) is to:
    - Scale out (add EC2 instances) to match an increased load
    - Scale in (remove EC2 instances) to match a decreased load
    - Ensure we have a minimum and a maximum number of EC2 instances running
    - Automatically register new instances to a load balancer
    - Re-create an EC2 instance in case a previous one is terminated (ex: if unhealthy)
- ASG are free (you only pay for the underlying EC2 instances)

## How does an ASG work?

An Auto Scaling Group (ASG) works by letting you define three settings: minimum, desired, and maximum capacity for EC2 instances. The ASG ensures that the number of instances never falls below the minimum, and it continually works to maintain the desired capacity — launching or terminating instances as needed. It can also scale out (add instances) up to the maximum capacity, and scale in (remove instances) when demand drops.

## Auto scaling group in AWS With Load Balancer

An Auto Scaling Group (ASG) is often integrated with a load balancer (ELB) to manage traffic distribution across its instances. The load balancer automatically routes incoming user traffic to all healthy EC2 instances within the group. It continuously performs health checks on these instances. If an instance fails a health check, the load balancer reports this to the ASG, which can then terminate the unhealthy instance and, depending on its configuration, launch a new one to replace it. This integration also ensures that when the ASG scales out (launches new instances), they are automatically registered with the load balancer and begin receiving traffic.

## Auto scaling group Attributes 

- A Launch Template (older “Launch Configurations” are deprecated)
    - AMI + Instance Type
    - EC2 User Data
    - EBS Volumes
    - Security Groups
    - SSH Key Pair
    - IAM Roles for your EC2 Instances
    - Network + Subnets Information
    - Load Balancer Information
- Min Size / Max Size / Initial Capacity
- Scaling Policies

## Auto scalling - Cloudwatch Alarms & Scaling

- It is possible to scale an ASG based on CloudWatch alarms
- An alarm monitors a metric (such as Average CPU, or a custom metric)
- Metrics such as Average CPU are computed for the overall ASG instances
- Based on the alarm:
    - We can create scale-out policies (increase the number of instances)
    - We can create scale-in policies (decrease the number of instances)

