# Gateway Load Balancer (GWLB)

- **Purpose:** Deploy, scale, and manage a fleet of 3rd party **network virtual appliances** in AWS.
  - Examples: **Firewalls**, **Intrusion Detection and Prevention Systems (IDPS)**, **Deep Packet Inspection (DPI)** systems, or any service performing **payload manipulation** at the **network level**.
- **Layer:** Operates at **Layer 3 (Network Layer)** — works directly with **IP packets**.
- **Core Functions:**
  - **Transparent Network Gateway:** Acts as a **single entry and exit point** for all network traffic within your VPC.
  - **Load Balancer:** Distributes network traffic across a target group of your virtual appliances.
- **Protocol:** Uses the **GENEVE protocol** on **port 6081** to encapsulate and forward traffic between the Gateway Load Balancer and its registered targets.
- **Common Use Case:** Forcing **all inbound and outbound traffic** through inspection or security layers before reaching your application or other VPC resources.

![GWLB](/4%20-%20AWS%20Fundamentals%20ELB%20ASG/images/7-GWLB.svg)

---

## How It Works

1. **Traffic Flow Concept**
   - Normally, users connect directly to your application via a standard load balancer (e.g., ALB).
   - With a **Gateway Load Balancer**, traffic is **routed first through the GWLB** before reaching your application.
   - This enables you to **inspect, filter, or modify** traffic **without changing the application architecture**.

2. **Routing & Transparency**
   - The **route tables** in your **VPC** are automatically **updated** to direct network traffic through the GWLB.
   - The process is **transparent** to both users and your applications — neither side needs to be aware of the inspection process.
   - Traffic:
     1. Arrives from users.
     2. Passes through the **Gateway Load Balancer**.
     3. Is distributed to **virtual appliances** in a **target group**.
     4. The appliances **inspect, accept, or drop** packets.
     5. Accepted traffic returns to the GWLB.
     6. GWLB forwards the traffic to your **application**.

3. **Security Enforcement**
   - If an appliance (e.g., firewall) **rejects** a packet, it is **dropped** before it reaches the target application.
   - If approved, traffic continues as normal, maintaining **network integrity** and **compliance**.

4. **Integration Simplicity**
   - Previously, inserting middleboxes (firewalls, IDS/IPS) into a network path required complex routing.
   - **GWLB** simplifies this by acting as a **transparent traffic hub**, automatically handling routing and distribution.


## Target Groups

- **Supported Targets:**
  - **EC2 Instances** — typically running 3rd-party network appliances (firewalls, security scanners, DPI systems).
  - **Private IP Addresses** — useful for appliances running on-premises or in other VPCs.
- **Registration Options:**
  - By **instance ID** (for EC2-based appliances).
  - By **private IP** (for hybrid or external appliances).

  ![GWLB-Target-Groups](/4%20-%20AWS%20Fundamentals%20ELB%20ASG/images/8-GWLB-Target-Group.svg)

