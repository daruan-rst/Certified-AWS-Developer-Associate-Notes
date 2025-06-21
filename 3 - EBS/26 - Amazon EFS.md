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
- File system scales automatically, pay-per-use, no capacity planning!

#### Performance
- EFS Scale
    - 1000s of concurrent NFS clients, 10+ GBs of thtoughput
    - Grow to Petabyte-scale network file system automatically
- Performance mode (set at EFS creation time)
    - General purpose(default) - latency-sensitive use cases (web server, CMS, etc ...)
- Thoughput mode
    - Bursting - 1TB = 50 MiB/s + burst of up to 100 MiB/s
    - Provisioned - set your thoughput regardless of storage size, ex: 1GiB/s for 1TB storage
    - Elastic - automatically scales thoughput up or down on your workloads
        - Up to 3 GiB/s for reads and 1 GiB/s for writes
        - Used for unpredicted workloads

<br><br>

#### Storage classes

- Storage tiers (lifecycle management feature - move file after N days)
    - Standard: for frequently accessed files
    - Infrequent Access (EFS-IA): cost to retrieve files, lower price to store. Enable EFS-IA with a lifecycle policy

- Availabilty and durability
    - Standart: multi-AZ, great for PROD
    - One zone: One AZ, great for dev, backup enabled by default, compatible with IA (EFS One Zone-IA)
    - Over 90% Savings 