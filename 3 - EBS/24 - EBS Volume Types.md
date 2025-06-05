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