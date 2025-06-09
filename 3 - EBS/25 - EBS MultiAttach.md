# EBS MultiAttach

## io1 / io2 family
 - Attach the same EBS volume to multiple EC2 instances in the same Availability zone
 -  Each instance has full read and write permissions to the high-performance volume 
 - Usecase: 
    - Achieve higher application availability in clustered Linux applications (Ex: Teradata) 
    - Applications must manage concurrent write operations
    <br><br>
    ![AMI-example](/3%20-%20EBS/images/3-EBS-MultiAttach.svg)


- Limitations: 
    - Only available from within a specified availability zone
        - Does not allow to attach one EBS volume from one availability zone to another availability zone 
    - Up to 16 ECV2 instances at a time can be attaching the same volume
    - Must use a file system that's cluster-aware (not XFS, EXT4, etc..)