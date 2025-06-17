# Amazon EFS - Elastic File System

-  Managed NFS (network file system) that can be mounted on many EC2
- EFS works with EC2 instances in multi-AZ  
- Highly available, scalable, expensive (3x gp2)
- Pay per use 

<br><br >

- Usecases: content management, web serving, datasharing, wordpress
- Uses NFSv4.1 protocol
- Uses security group to control access to EFS
- Compatible with Linux based AMI (not Windows)
- Encryption at rest using KMS


<br><br>

- POSIX File System (~Linux) that has a standart file API