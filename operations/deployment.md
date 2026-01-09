# Automated Application Deployment

## Purpose
This document explains how the application is deployed automatically on EC2 instances without manual intervention.

Automation ensures consistency, reliability, and scalability.

---

## Problem With Manual Deployment
Manually deploying applications using SSH introduces multiple risks:

- Human error during setup
- Inconsistent server configuration
- Delays during failure recovery
- Inability to scale automatically

Manual deployment does not work in production systems.

---

## Deployment Strategy Overview
The application is deployed automatically using EC2 User Data.

This approach ensures that every new instance:
- Is configured the same way
- Installs required software
- Starts required services
- Becomes ready without human involvement

---

## Role of User Data
User Data is a startup script executed when an EC2 instance boots for the first time.

It performs the following actions:
- Updates the operating system
- Installs Nginx
- Starts and enables the web service
- Deploys the application files

This process happens automatically for every instance.

---

## Integration With Auto Scaling
Auto Scaling Groups rely on User Data for deployment.

When an instance is launched:
- The Launch Template defines the User Data script
- The script configures the instance
- The instance passes health checks
- Traffic is routed automatically

No manual SSH access is required.

---

## Deployment During Failure Recovery
During failure simulations:
- Instances were terminated intentionally
- New instances were launched automatically
- Application deployment completed without intervention
- Traffic was restored through the Load Balancer

This confirms the effectiveness of automated deployment.

---

## Engineering Outcome
By using automated deployment:
- Server setup is repeatable
- Recovery is predictable
- Human dependency is reduced
- The system behaves reliably under failure

Automation is a core requirement for production systems.
