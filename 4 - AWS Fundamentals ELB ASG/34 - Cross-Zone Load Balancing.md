# Cross-Zone Load Balancing

![Cross-Zone-Load-Balancing](/4%20-%20AWS%20Fundamentals%20ELB%20ASG/images/10-Cross-Zone-Load-Balancing.svg)


- Application Load Balancer
    - Enabled by default (can be disabled at the Target Group Level)
    - No charges for inter AZ data

- Network Load Balancer & Gateway Load Balancer
    - Disabled by default
    - You pay charges for inter AZ data if enabled

- Classic Load Balancer
    - Disabled by default