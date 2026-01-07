# Application Load Balancer (ALB)

## Purpose
The Application Load Balancer (ALB) is the single entry point for all user traffic in this architecture.

Users never connect directly to EC2 instances.
All requests are routed through the Load Balancer.

This design ensures availability, scalability, and fault tolerance.

---

## Problem Without a Load Balancer
If users connect directly to a single EC2 instance:
- The server becomes a single point of failure
- Any crash causes complete downtime
- Scaling traffic is not possible
- IP address changes break access

This approach is not suitable for production systems.

---

## Role of the Application Load Balancer
The ALB solves these problems by:
- Providing a stable DNS endpoint for users
- Distributing traffic across multiple EC2 instances
- Performing health checks on backend servers
- Automatically stopping traffic to unhealthy instances

The Load Balancer protects users from backend failures.

---

## Traffic Flow
The request flow works as follows:

1. User sends request to ALB DNS
2. ALB receives the request
3. ALB forwards the request to a healthy EC2 instance
4. EC2 processes the request and responds
5. ALB returns the response to the user

At no point does the user interact directly with EC2.

---

## Target Groups
The ALB routes traffic to a Target Group.

The Target Group:
- Contains EC2 instances managed by Auto Scaling
- Tracks health status of each instance
- Sends traffic only to healthy targets

If an instance becomes unhealthy, it is automatically removed from traffic.

---

## Health Checks
Health checks are performed on the path `/`.

- The ALB sends periodic HTTP requests
- A `200 OK` response marks the instance healthy
- Failures mark the instance unhealthy

This allows the system to detect problems automatically.

---

## High Availability
The ALB is deployed across multiple public subnets.

This ensures:
- Traffic remains available even if one subnet fails
- Users can always reach the application
- Backend instances can scale independently

---

## Engineering Outcome
By using an Application Load Balancer:
- User traffic is stable and predictable
- Backend servers are replaceable
- Failures are isolated
- The system behaves like a production environment

The Load Balancer is a critical component for reliability.
