# EC2 Instances Purchasing Options

## EC2 On Demand
- Pay for what you use:
    - Linux or Windows - billing per second, after the first minute
    - All other operating systems - billing per hour
- Has the highest cost, but no upfront payment
- No long-term commitment
- Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave

## EC2 Reserved Instances
- Up to 72% discount compared to on-demmand
- The attributes of the instance must be reserved:
    - Instance type
    - Region
    - Tenancy
    - OS
- Reservation Period:
    - 1 year (has a discount compared to on demand)
    - 3 years (even higher discount compared to on demand)
- Reserved Instance's scope: Regional or Zonal (Reserve Capacity in an AZ)
- Recommended for steady-state usage applications
    - Ex: Databases
- You can buy and sell in the Reserved Instances Marketplace

#### Convertible Reserved Instances
- Can change the EC2 instance type, instance family, OS, scope and tenancy
- Up to 66% discount

## EC2 Savings Plan
- Get a discount based on long-term usage (up t0 72% - same as Reserved Instances)
- Commit to a certain type of usage (%10,00/hour)
- Usage beyond EC2 savings plans is billed at the on-demmand price
- Locked to a specific instance family and AWS region (e.g. m5 in US-EAST-1)
- Flexible across:
    - Instance Size (e.g. m5.xlarge, m5.2xlarge)
    - OS (e.g. Linux, Windows)
    - Tenancy (Host, Dedicated, Default)

## EC2 Spot Instances

- Can get a discount of up to 90% compared to on-demand
- Instances that you can "lose" at any point of time if you max price is less than  the current spot price
- The MOST cost-efficient instances in AWS 
- Useful for workloads that are resilient to failure:
    - Batch jobs
    - Data Analysis
    - Image Processing
    - Any distributed workloads
- Not suitable fot critical jobs or databases

## EC2 Dedicated Hosts
- A physical server with EC2 instance capacity fully dedicated to your usecase
- Allows you to address compliance requirements and use your existing server-bound software licenses (per-socket, per-core, per-VM software licenses)
- Purchasing options: 
    - On-demand: pay per second for active dedicated host
    - Reserved: 1 or 3 years (No upfront, Partial Upfront or All upfront)
- The most expensive option
- Useful for software that have complicated licensing model (BYOL - Bring you own license)
- Useful for companies that have strong regulatory or compliance needs

## EC2 Dedicated Instances
- Instances run on hardware that's dedicated to you
- May share hardware with other instances in the same account
- No control over instances placement (can move hardware after Stop/Start)

|                 Characteristic                | Dedicated Instances | Dedicated Hosts |
|:---------------------------------------------:|:-------------------:|:---------------:|
| Enables the use of dedicated physical servers |          X          |        X        |
|              Per instance billing             |          X          |                 |
|                Per host billing               |                     |        X        |
|     Visibility of sockets, cores, host ID     |                     |        X        |
|     Affinity between a host and instance      |                     |        X        |
|          Targeted instance placement          |                     |        X        |
|          Automatic instance placement         |          X          |        X        |
|    Add capacity using an allocation request   |                     |        X        |

**Table 1:** *Differences between Dedicated Instances and Dedicated Hosts*

## EC2 Capacity Reservations
- Reserve On-Demmand instnaces capacity in a specific AZ for any duration
- You always have access to EC2 capacity when you need it
- No time commitment (create/ cancel anytime), no billing discounts
- The only purpose is to reserve capacity 
- Combine with regional reserved instances and Saving Plans to benefit from billing discounts
- You're charged at on-demmand rate whether you run instances or not
- Suitable for short-term, uninterrupted workloads that need to be in a specific AZ

---

## Summary Table

| Pricing Model       | Commitment | Flexibility | Potential Savings | Ideal For                                 |
|---------------------|------------|-------------|-------------------|-------------------------------------------|
| On-Demand           | None       | High        | None              | Short-term, unpredictable workloads       |
| Reserved Instances  | 1 or 3 yrs | Low         | Up to 72%         | Steady-state, predictable workloads       |
| Savings Plans       | 1 or 3 yrs | Medium      | Up to 72%         | Consistent usage with some flexibility    |
| Spot Instances      | None       | High        | Up to 90%         | Fault-tolerant, flexible applications     |
| Dedicated Hosts     | 1 or 3 yrs | Low         | Varies            | Compliance and licensing requirements     |
| Capacity Reservations| Flexible  | Medium      | None              | Guaranteed capacity needs                 |

---

