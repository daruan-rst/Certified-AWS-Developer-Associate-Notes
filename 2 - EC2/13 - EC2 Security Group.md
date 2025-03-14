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

    ![EC2SecurityGroupDiagram](/2%20-%20EC2/images/2-SecurityGroupDiagram.svg)