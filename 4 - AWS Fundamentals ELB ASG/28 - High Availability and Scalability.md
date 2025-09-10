# High Availability and Scalability

## Scalability

- Scalability means that an application / system can handle greater loads by adapting
- There are two kinds of scalability:
    - Vertical Scalability
    - Horizontal Scalability (= elasticiy)
- Scalability is linked but different to High Availability

### Vertical Scalability
- Vercally scalability means increasing the size of the instance
    - For example: if your application runs on a t2.micro, than vertically scaling it would mean running it on a t2.large
- Vertical scalability is very common for non distributed systems, such as a database
- RDS, ElastiCahe are services that can scale vertically
- There is usually a limit to how much you can vertically scale (hardware limit)

### Horizontal Scalability
- Horizontal scalability means increasing the number of instances / systems for your application.
    - For example: if your application runs on a single t2.micro, than zorizontally scaling it would mean running it on two or more t2.micro instances.
- Horizontally scaling implies distributed systems.
- This is very common for web applications / modern applications
- It's easy to horizontally scale thanks to cloud offerings syc as Amazon EC2

## High Availability
- High High Availability usually goes hand in hand with horizontal scaling
- High availability means running your application / system in at least 2 data centers (== Availability Zones)
- The goal of high High availability is to survive a data center loss
- The high availability can be passive (for RDS Multi AZ for example)
- The high availability can be active (for horizontal scaling)

### High Availability & Scalability for EC2
- Vertical Scaling: Increase instance size (= scale up / down)
    - From: t2.nano - 0.5G of RAM, l vCPU
    - To: u -l2tbl.metal - 12.3 TB of RAM, 448 vCPUs

- Horizontal Scaling: Increase number of instances (= scale out / in)
    - Auto Scaling Group
    - Load Balancer

- High Availability: Run instances for the same application across multi AZ
