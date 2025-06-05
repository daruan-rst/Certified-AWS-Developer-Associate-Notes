# EBS Volume Types

- There are 6 types of EBS Volumes:
    - gp2/gp3 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads
    - io1 / io2 (SSD): Highest performance SSD volume for mission-critical low-latency or high-troughput workloads
    - st1 (HDD): Low cost HDD volume designed for frequently accessed, troughput-intensive workloads
    - sc1 (HDD): Lowest cost HDD volume designed for less frequently accessed workloads

- EBS Volumes are charecterized in Size, Throughput and IOPS (**I**nputs/**O**utputs **p**er **s**econd)
- Only gp2/gp3 and io1/io2 can be used as boot volumes

<br><br>
### EBS Volume types Use cases
#### General purpose SSDs
- Cost effective storage, low-latency
- System boot volumes, Virtual desktops, Development and test environments
- The size can vary between 1Gb to 16TB
- gp3: 
    - Baseline of 3000 IOPS and thoughput of 125MiB/s
    - Can increase the IOPS up to 16000 and throughput up to 1000 MiB/s independently  
- gp2: 
    - Small gp2 volumes can burst IOPS to 3000
    - Size of the volume and IOPS are linked, max IOPS is 16000
    - 3 IOPS per GB, means at 5334 GB we are at the max IOPS

