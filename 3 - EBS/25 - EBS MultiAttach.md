# EBS MultiAttach

## io1 / io2 family
 - Attach the same EBS volume to multiple EC2 instances in the same Availability zone
 -  Each instance has full read and write permissions to the high-performance volume 
 - Usecase: 
    - Achieve higher application availability in clustered Linux applications (Ex: Teradata) 