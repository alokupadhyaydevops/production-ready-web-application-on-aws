# Networking and Traffic Isolation

## Purpose
This document explains how network design controls traffic flow and protects backend servers.

The goal is to expose only what is required while keeping internal components isolated.

---

## Network Design Overview
The system is designed with clear traffic boundaries:

- The Application Load Balancer is publicly accessible
- EC2 instances are accessed only through the Load Balancer
- Users never connect directly to backend servers

This layered approach improves security and reliability.

---

## Public Entry Point
The Application Load Balancer is deployed in public subnets.

Reasons:
- It must accept traffic from the internet
- It provides a single, stable DNS endpoint
- It distributes traffic across backend instances

The Load Balancer is the only internet-facing component.

---

## Backend Isolation
EC2 instances are not intended to be accessed by users directly.

Security controls ensure:
- EC2 instances accept traffic only from the Load Balancer
- No public IP exposure is required for application access
- Backend servers remain hidden from the internet

This reduces the attack surface significantly.

---

## Security Groups as Network Firewalls
Security Groups control traffic between components.

Typical behavior:
- ALB Security Group allows inbound HTTP from the internet
- EC2 Security Group allows inbound HTTP only from the ALB
- SSH access is restricted for administration

This enforces strict communication rules.

---

## Traffic Flow Summary
The allowed traffic flow is:

1. Internet → Application Load Balancer
2. Application Load Balancer → EC2 instances
3. EC2 instances → Respond back through ALB

Any traffic outside this path is blocked by design.

---

## Engineering Outcome
By controlling network exposure:
- Backend servers are protected
- User traffic is predictable
- Failures are isolated
- Security risks are minimized

This networking design supports production-grade systems.
