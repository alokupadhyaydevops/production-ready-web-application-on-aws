# Auto Scaling Group (ASG)

## Purpose
The Auto Scaling Group (ASG) is responsible for maintaining the correct number of EC2 instances in the system.

It ensures that instances are:
- Automatically created
- Automatically replaced if they fail
- Always available to serve traffic

The ASG removes manual intervention from server management.

---

## Problem Without Auto Scaling
Without an Auto Scaling Group:
- A failed EC2 must be replaced manually
- Downtime depends on human response time
- Traffic cannot be handled reliably
- Systems are fragile and error-prone

This approach is not acceptable in production environments.

---

## Role of the Auto Scaling Group
The ASG continuously monitors the number and health of EC2 instances.

Its responsibilities include:
- Launching new instances when required
- Replacing unhealthy or terminated instances
- Ensuring minimum capacity is always met

The ASG does not configure servers.
It creates instances based on a predefined blueprint.

---

## Launch Template
The Launch Template defines how every EC2 instance should be created.

It includes:
- Amazon Machine Image (AMI)
- Instance type
- Security Groups
- IAM Role
- User Data (automatic setup)

All instances created by the ASG are identical and disposable.

---

## Automated Instance Configuration
User Data is used to configure instances at boot time.

This ensures that:
- Nginx is installed automatically
- The application is deployed automatically
- No manual SSH access is required

Automation is mandatory for scalable systems.

---

## Health Checks and Replacement
The ASG works together with the Load Balancer health checks.

If an instance:
- Fails health checks
- Is terminated manually
- Becomes unavailable

The ASG automatically launches a replacement instance.

This replacement happens without user impact.

---

## Failure Recovery Behavior
During failure simulations:
- Instances were intentionally terminated
- Traffic continued flowing through healthy instances
- New instances were launched automatically
- System stability was restored without manual action

This confirms self-healing behavior.

---

## Engineering Outcome
By using an Auto Scaling Group:
- Servers become disposable
- Failures are expected and handled
- Human dependency is reduced
- The system behaves predictably under failure

The ASG is a core component of production resilience.
