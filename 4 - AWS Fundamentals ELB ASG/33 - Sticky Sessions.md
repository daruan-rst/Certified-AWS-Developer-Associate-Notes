# Sticky Sessions (Session Affinity)
- It is possible to implement stickiness so that the
same client is always redirected to the same
instance behind a load balancer
- This works for Classic Load Balancer,
Application Load Balancer, and Network Load
Balancer
- For both CLB & ALB, the “cookie” used for
stickiness has an expiration date you control
- Use case: make sure the user doesn’t lose his
session data
- Enabling stickiness may bring imbalance to the
load over the backend EC2 instances