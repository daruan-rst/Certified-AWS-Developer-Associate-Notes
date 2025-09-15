# Application Load Balancer

- Application load balancers is Layer 7 (HTTP)
- Load balancing to multiple HTTP applications across machines
(target groups)
- Load balancing to multiple applications on the same machine
(ex: containers)
- Support for HTTP/2 and WebSocket
- Support redirects (from HTTP to HTTPS for example)

- Routing tables to different target groups:-
    - Routing based on path in URL (example.com/users & example.com/posts)
    - Routing based on hostname in URL (one.example.com & other.example.com)
    - Routing based on Query String, Headers
(example.com/users?id=123&order=false)
- ALB are a great fit for micro services & container-based application
(example: Docker & Amazon ECS)
- Has a port mapping feature to redirect to a dynamic port in ECS
- In comparison, we’d need multiple Classic Load Balancer per application


## HTTP Based Traffic

- An Application Load Balancer (ALB) can route **multiple applications behind a single load balancer**.
- Example setup:
  - ALB (public-facing) receives traffic.
  - Target Group 1: EC2 instances serving the **/user** route.
  - Target Group 2: EC2 instances serving the **/search** route.
- Each target group has **health checks** to ensure traffic only goes to healthy instances.
- This enables **independent microservices** (e.g., user service and search service) to coexist behind the same ALB.
- The ALB uses **routing rules** to direct traffic based on the **URL path** (e.g., `/user`, `/search`).

## Target Groups
- EC2 instances (can be managed by an Auto Scaling Group) – HTTP
- ECS tasks (managed by ECS itself) – HTTP
- Lambda functions – HTTP requests are translated into JSON events (less known use case, enables serverless behind ALB)
- IP addresses – must be private IPs, including on-premises servers (via private IP registration)
- ALB can route to multiple target groups simultaneously
- Health checks are defined and executed at the target group level


