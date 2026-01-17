# Rollback Strategy

This document defines how rollback would be handled in this infrastructure without CI/CD automation.

## Scenario

A new application change is deployed manually to the EC2 instances.
After deployment:
- The website becomes unstable, or  
- Users start reporting errors, or  
- Health checks begin failing  

A rollback is required to restore service quickly.

## Rollback Approach (Manual but Controlled)

In this project, rollback is handled at the infrastructure and operations level:

1. The previous working version of the application is preserved locally on the server  
2. If a failure occurs, the web server configuration is restored to the previous version  
3. The Application Load Balancer health checks confirm recovery  
4. Auto Scaling ensures unhealthy instances are replaced if recovery fails  

## Why this matters

This simulates real-world production practices where:
- Not all systems have automated rollback  
- Engineers must understand how to recover systems manually  
- Stability and recovery procedures are critical  

## What this demonstrates

- Understanding of operational reliability  
- Awareness of failure scenarios  
- Knowledge of recovery techniques  
- Production mindset, not just deployment success  
