# Auto Scaling Group Instance Failure and Recovery

## Overview
This document describes a controlled failure simulation performed on a production-style AWS architecture using an Application Load Balancer (ALB) and an Auto Scaling Group (ASG).

The goal was to validate self-healing behavior and observe system response without manual intervention.

---

## Architecture Context
- Application Load Balancer (internet-facing)
- Auto Scaling Group (minimum 2 instances)
- EC2 instances running Nginx
- Health checks configured on `/`
- Monitoring via CloudWatch

Users access the system only through the ALB DNS.

---

## Failure Scenario 1: Single Instance Termination

### Action Taken
One EC2 instance created by the Auto Scaling Group was manually terminated to simulate partial failure.

### Observations
- Target Group healthy host count dropped from 2 to 1
- Application remained accessible via ALB
- No user-visible downtime occurred

### Recovery Behavior
- Auto Scaling Group detected the missing instance
- A new EC2 instance was launched automatically
- User Data installed and started Nginx
- New instance registered as healthy
- Healthy host count returned to 2

---

## Failure Scenario 2: Complete Instance Loss

### Action Taken
All EC2 instances managed by the Auto Scaling Group were terminated to simulate full server loss.

### Observations
- Target Group temporarily showed zero healthy instances
- ALB had no healthy backends briefly
- Auto Scaling Group immediately began recovery

### Recovery Behavior
- New EC2 instances were launched automatically
- Application stack installed via User Data
- Instances passed health checks
- Application became accessible again without manual intervention

---

## Monitoring Observations
- CloudWatch metrics showed changes in HealthyHostCount
- CPU metrics reset for newly launched instances
- No alarms were triggered during normal recovery

---

## Engineering Takeaways
- Servers are disposable resources
- Auto Scaling Groups provide self-healing behavior
- Load Balancers protect users from backend failures
- Monitoring provides visibility without manual checks

This simulation demonstrates production-grade resilience and validates the architecture design.
