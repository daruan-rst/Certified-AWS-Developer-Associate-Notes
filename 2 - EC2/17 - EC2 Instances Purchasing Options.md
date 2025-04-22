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