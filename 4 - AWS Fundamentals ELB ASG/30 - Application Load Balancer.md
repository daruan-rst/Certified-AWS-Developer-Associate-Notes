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

### Basic Setup
- ALBs are created as **Internet-facing** or **internal**.
- They provide a **DNS name** automatically to route client traffic.
- Deployed across **multiple Availability Zones** for high availability.
- Listeners (e.g., port 80 for HTTP) forward traffic to **target groups**.


## HTTP Based Traffic

- An Application Load Balancer (ALB) can route **multiple applications behind a single load balancer**.
- Example setup:
  - ALB (public-facing) receives traffic.
  - Target Group 1: EC2 instances serving the **/user** route.
  - Target Group 2: EC2 instances serving the **/search** route.
- Each target group has **health checks** to ensure traffic only goes to healthy instances.
- This enables **independent microservices** (e.g., user service and search service) to coexist behind the same ALB.
- The ALB uses **routing rules** to direct traffic based on the **URL path** (e.g., `/user`, `/search`).

## Target Health & Failover
- ALB continuously monitors registered targets with **health checks**.
- If a target (e.g., an EC2 instance) becomes unhealthy or is stopped:
  - ALB automatically stops routing traffic to it.
  - When the target recovers and passes health checks again, ALB resumes sending traffic.
- Demonstrated by stopping/starting EC2 instances — traffic seamlessly shifted to healthy targets.

## Target Groups
- EC2 instances (can be managed by an Auto Scaling Group) – HTTP
- ECS tasks (managed by ECS itself) – HTTP
- Lambda functions – HTTP requests are translated into JSON events (less known use case, enables serverless behind ALB)
- IP addresses – must be private IPs, including on-premises servers (via private IP registration)
- ALB can route to multiple target groups simultaneously
- Health checks are defined and executed at the target group level

## Query Strings / Parameter Routing
- ALB can route traffic based on **query string parameters** in the URL.  
- Example scenario:
  - ALB has two target groups:
    - Target Group 1: EC2 instances in AWS.
    - Target Group 2: On-premises private servers (registered via private IPs).
- Rule-based routing example:
  - If the URL contains `?Platform=Mobile` → route to **Target Group 1**.
  - If the URL contains `?Platform=Desktop` → route to **Target Group 2**.
- This demonstrates how ALB can apply **fine-grained routing** decisions using query strings or parameters.
- Tutor note: Example use case is illustrative — real-world usage may vary.

## Advanced Rule Features
- Rules can define custom behaviors:
  - **Fixed responses** (e.g., return a 404 error with a custom message if path = `/error`).
  - **Redirects** (e.g., `/old-path` → `/new-path` or enforce HTTPS).
  - **Forwarding** to other target groups based on conditions (host header, path, query string, headers).
- Rules are evaluated in order, allowing flexible routing logic.

## Security Best Practices
- Use **separate security groups**:
  - ALB security group: allow HTTP/HTTPS from the internet.
  - EC2 target security group: only allow inbound traffic **from the ALB security group** (not from the internet directly).
- Prevents bypassing the ALB by accessing EC2 instances directly.

## Comparison with Other Load Balancers
- **ALB (Application Load Balancer)**: Layer 7, for HTTP/HTTPS, supports advanced routing.
- **NLB (Network Load Balancer)**: Layer 4, TCP/UDP/TLS, ultra-high performance, millions of requests/sec with low latency.
- **GLB (Gateway Load Balancer)**: Integrates with security appliances (firewalls, IDS/IPS) to inspect network traffic.
- **CLB (Classic Load Balancer)**: Legacy, being phased out.
