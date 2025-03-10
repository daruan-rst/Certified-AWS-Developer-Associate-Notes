# EC2 - Instance Types
- It is possible to select different types of EC2 instances that are optimised for different usecases
- AWS has the following naming convention:

```
    m5.2xlarge
```
- m: instance
- 5: generation
- 2xlarge: size within the instance class

## Types
#### General Purpose
- Great for a diversity of workloads such as webservers or code repositories
- Good Balance Between:
    - COmpute
    - Memory
    - Networking

#### Compute Optimized
- Great for compute-intensive tasks that require high performance processors
- Procedures like:
    - Batch processing workloads
    - Media transcoding
    - High performance web servers
    - Scientific modeling & machine learning
    - Dedicated gaming servers

#### Memory Optimized:
- Fast performance for workloads that process large datra sets in memory (RAM)
- Usecases: 
    - High performance. relational / non relational databases
    - Distributed web scale cache stores
    - In memory databases for BI
    - Applications performing real-time processing of big unstructured data

#### Storage Optimized
- Great for storage-intensive tasks that require high, sequential read anbd write access to large datasets on local storage
- Usecases:
    - High frequency online transaction processing (OLTP)
    - Relational and non relational databases
    - Cache for in-memory databases
    - Data warehousing applications
    - Distributed File Systems
- The EC2 User data script runs with the root user