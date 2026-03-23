# Auto Scalling Groups - Dynamic Scaling Policies

 - Target Tracking Scaling
    - Most simple and easu to set-up
    - Example: I want the average ASG CPU to stay at around 40%

- Simple / Step Scaling
    - When a CloudWatch alarm is triggered (example CPU > 70% ), then add 2 units
    - When a CloudWatch alarm is triggered (example CPU < 30% ), then remove 1 unit

- Schedule Actions
    - Anticipate a scaling based on knwown usage pattern
    - Example: increase the min capacity to 10 at 5 pm on Fridays

- Predictive Scaling
    - Continuously forecast load and schedule scaling ahead

____

### Good metrics to scale on
- CPUUtilization: Average CPU utilization across your instances
- RequestCoutPerTarget: to make sure the number of request per EC2 instances is stable
- Average Network In / Out : (if you're application is network bound)
- Any custom metric: it is possible to set a customized metric using CloudWatch

### Auto Scalling Groups - Scaling Cooldowns

- After a scaling activity happens, you are in the cooldown period (default 300 seconds)
- During the cooldown pedior, the pASD will not launch or terminate additional instances (to allow for metrics to stabilize )

- Advice: Use a ready-to-use AMI to reduce configuration time in order to be serving request fasters and reduce the cooldown period