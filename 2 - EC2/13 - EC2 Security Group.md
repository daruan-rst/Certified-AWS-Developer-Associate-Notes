# EC2 Security Group

- Security Groups are the fundamental of network security in AWS
- They control how traffic is allowed into or out of our EC2 instances

![EC2SecurityGroup](/2%20-%20EC2/images/1-SecurityGroup1.svg)

- Security Group only contain  <span style="color:green">allow</span> rules
- Security Groups can only reference by IP or by Security Group
- A security group can be created "around" an EC2 instance - resambling a firewall - which may have rules to determine whether or not some inbound or outbound traffic from the outside into the EC2 is allowed
- A security group may also allow (or block) an EC2 instance to perform some outbound traffic
- Security Groups are acting as a "firewall" on EC2 instances
- They Regulate:
    - Access to ports
    - Authorized UP ranges - IPV4 or IPV6
    - Control of Inbound Network (from other to the instance)
    - Control of Outbound Network (from the instance to other)

#### Security Group Diagram

![EC2SecurityGroup](/2%20-%20EC2/images/2-SecurityGroupDiagram.svg)

## Security Groups Good to know

- Can be attatched to multiple instances
- An instance can have multiple security groups
- Locked down to a region / VPC combination
- Lives "outside" the EC2 - if traffic is blocked the EC2 instance won't see it
- It's good to mantain one separate security group for ssh access
- If an application is not accessible (time out) then it's a security group issue
- If an application returns a "connection refused" error, then it's an application error or it's not launched
- By default:
    - All inbound traffic is blocked
    - All outbound traffic is allowed

## Referencing other seucrity groups 

![ReferencingSecurityGroups](/2%20-%20EC2/images/3-ReferencingOtherSecurityGroups.svg)

- Security groups can reference other security groups, allowing instances with specific security groups to comunicate. 

## Common Ports to Know
- **SSH (Secure Shell)**: Port 22 (Linux instance login).
- **FTP (File Transfer Protocol)**: Port 21 (file uploads).
- **SFTP (Secure File Transfer Protocol)**: Port 22 (file uploads using SSH).
- **HTTP**: Port 80 (unsecured websites).
- **HTTPS**: Port 443 (secured websites).
- **RDP (Remote Desktop Protocol)**: Port 3389 (Windows instance login).