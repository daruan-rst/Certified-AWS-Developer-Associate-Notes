# Network Load Balancer

- Network load balancers (Layer 4) allow to:
  - Forward TCP & UDP traffic to your instances
  - Handle millions of request per seconds
  - Ultra-low latency
- NLB has one static IP per AZ, and supports assigning Elastic IP
(helpful for whitelisting specific IP)
- NLB are used for extreme performance, TCP or UDP traffic
- Not included in the AWS free tier

![NLB-HTTP-Based-Traffic](/4%20-%20AWS%20Fundamentals%20ELB%20ASG/images/5-NLB-HTTP-Based-Traffic.svg)

### Setup & IP Addressing
- NLB can be **Internet-facing** (public) or **internal**.
- When deployed across multiple AZs, each AZ gets **one fixed IP**.
- Option to assign **Elastic IPs** instead of AWS-assigned IPs:
  - Helpful for **whitelisting static IPs** in firewalls or external integrations.
- In the demo: created an **Internet-facing NLB** across **3 AZs** → resulted in **3 fixed IPs**.


### Target Groups

- EC2 instances
- IP Addresses – must be private IPs
- Application Load Balancer
- Health Checks support the TCP, HTTP and HTTPS Protocols

![NLB-Target-Groups](/4%20-%20AWS%20Fundamentals%20ELB%20ASG/images/6-NLB-Target-Groups.svg)



### Target Group Configuration
- Created a **target group for instances** (`demo-tg-nlb`).
- Protocol: **TCP on port 80**.
- Health check options:
  - TCP, HTTP, or HTTPS.
  - If the application is HTTP-based, using HTTP health checks with a path (e.g., `/`) is recommended.
- Example health check config:
  - Path: `/`
  - Healthy threshold: 2
  - Timeout: 2 seconds
  - Interval: 5 seconds

### Behavior & Security Considerations
- **NLBs do not use security groups**.
  - All traffic is passed directly to the registered targets.
  - The **EC2 instance security group** is responsible for allowing or denying traffic.
- Issue observed:
  - Instances were marked **unhealthy** because their SG only allowed port 80 from the ALB SG.
  - Fix: temporarily allowed **HTTP (port 80) from anywhere** in the EC2 SG.
- After fixing the SG:
  - Health checks turned **healthy**.
  - NLB began distributing requests properly across instances.

### Observed Behavior
- Accessing the NLB’s DNS name showed the web app (`Hello World`).
- Refreshing alternated responses between EC2 instances (round-robin).
- Demonstrated **high availability** and **load distribution**.

### Best practice after testing:
  - Delete the NLB.
  - Delete the associated target group.
  - Revert EC2 security group rules to remove temporary “allow from anywhere” entries.
