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

<br><br>

#### Provisioned IOPS (PIOPS) SSD
- Critical business applications with sustained IOPS performance
- Applicaitons that need more than 16000 IOPS
- Great for database workloads (sensitive to storage performance and consistency)
- io1 / io2 ( 4GiB - 16 GiB)
    - Max PIOPS: 64000 for Nitro EC2 instances & 32000 for other
    - Can increase PIOPS independently from storage size
- io2 Block Express (4 GiB - 64 GiB)
    - Sub-milliosecond latency
    - Max PIOPS: 256000 with an IOPS: GiB ratio of 1000 : 1
- Supports EBS Multi-attatch

#### Hard Disk Drives (HDD)
- Cannot be a boot volume
- 125 GiB to 16 TiB
- Throughput Optimized HDD (st1)
    - Big Data, Data Warehouses, Log Processing
    - Max throughput of 500 MiB/s - max IOPS 500  
- Cold HDD (sc1)
    - For data that is infrequently accessed
    - Scenarios where lowest cost is important
    - Max throughput 250 MiB/s - max IOPS 250