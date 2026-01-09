# Production-Ready Web Application on AWS

## Overview
This project demonstrates the design and implementation of a production-style web application architecture on AWS.

The focus is not on application complexity, but on building a reliable, scalable, and self-healing infrastructure that reflects real-world engineering practices.

---

## Project Goals
- Eliminate single points of failure
- Ensure automatic recovery from instance failures
- Protect users from backend instability
- Remove manual server dependency
- Observe system behavior through monitoring

This project is designed to reflect how production systems are built and operated.

---

## Architecture Summary
The system is composed of the following core components:

- Application Load Balancer (ALB) as the single public entry point
- Auto Scaling Group (ASG) maintaining multiple EC2 instances
- Automated application deployment using EC2 User Data
- Health checks to control traffic flow
- IAM Roles for secure, keyless AWS access
- CloudWatch monitoring for visibility
- Cost awareness and safe shutdown strategy

Users interact only with the Load Balancer.
Backend servers are fully replaceable.

---

## Key Engineering Principles Demonstrated
- **High Availability**: Traffic continues during instance failures
- **Automation First**: No manual SSH-based deployment
- **Security by Design**: No hardcoded credentials or public EC2 access
- **Self-Healing Infrastructure**: Instances are replaced automatically
- **Operational Visibility**: Metrics and alarms provide insight into system health

---

## Failure Simulation and Recovery
Intentional failure simulations were performed to validate resilience:

- Individual EC2 instances were terminated
- Complete backend loss was simulated
- Auto Scaling and Load Balancer behavior was observed
- Recovery occurred without manual intervention

These scenarios are documented in the `failure-scenarios/` directory.

---

## Repository Structure
# Production-Ready Web Application on AWS

## Overview
This project demonstrates the design and implementation of a production-style web application architecture on AWS.

The focus is not on application complexity, but on building a reliable, scalable, and self-healing infrastructure that reflects real-world engineering practices.

---

## Project Goals
- Eliminate single points of failure
- Ensure automatic recovery from instance failures
- Protect users from backend instability
- Remove manual server dependency
- Observe system behavior through monitoring

This project is designed to reflect how production systems are built and operated.

---

## Architecture Summary
The system is composed of the following core components:

- Application Load Balancer (ALB) as the single public entry point
- Auto Scaling Group (ASG) maintaining multiple EC2 instances
- Automated application deployment using EC2 User Data
- Health checks to control traffic flow
- IAM Roles for secure, keyless AWS access
- CloudWatch monitoring for visibility
- Cost awareness and safe shutdown strategy

Users interact only with the Load Balancer.
Backend servers are fully replaceable.

---

## Key Engineering Principles Demonstrated
- **High Availability**: Traffic continues during instance failures
- **Automation First**: No manual SSH-based deployment
- **Security by Design**: No hardcoded credentials or public EC2 access
- **Self-Healing Infrastructure**: Instances are replaced automatically
- **Operational Visibility**: Metrics and alarms provide insight into system health

---

## Failure Simulation and Recovery
Intentional failure simulations were performed to validate resilience:

- Individual EC2 instances were terminated
- Complete backend loss was simulated
- Auto Scaling and Load Balancer behavior was observed
- Recovery occurred without manual intervention

These scenarios are documented in the `failure-scenarios/` directory.

---

## Repository Structureinfrastructure/
load-balancer.md
auto-scaling.md
networking.md

operations/
deployment.md
health-checks.md

failure-scenarios/
asg-instance-failure-and-recovery.md

app/
index.html


---

## Outcome
This project demonstrates production-oriented thinking rather than simple service usage.

It reflects how real-world systems are designed to tolerate failure, scale safely, and remain observable without relying on human intervention.

---

## Notes
This project intentionally uses a simple application to keep focus on infrastructure behavior, reliability, and operations.

