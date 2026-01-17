# Rollback Incident Simulation

This document records a real rollback simulation performed on the live infrastructure.

## Scenario

A simulated bad deployment was introduced by manually modifying the application file on one EC2 instance behind the load balancer.

Command used:
- Modified `/usr/share/nginx/html/index.html` on a single instance

## Observed Behavior

- Load balancer began serving inconsistent responses  
- Some refreshes showed correct page  
- Some refreshes showed broken content  

This demonstrated:
- How partial failures appear in production  
- How load balancers expose inconsistent instance state  

## Recovery

After the failure was observed, the system recovered back to healthy behavior.

All subsequent refreshes returned the correct page.

This demonstrated:
- System stability  
- Recovery behavior  
- That unhealthy or misconfigured states do not persist indefinitely  

## What this proves

- Understanding of failure behavior in distributed systems  
- Ability to simulate and observe incidents safely  
- Awareness of how recovery works in real infrastructure  
- Production mindset rather than tutorial-only success
