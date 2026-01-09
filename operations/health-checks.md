# Health Checks and Service Readiness

## Purpose
This document explains how the system determines whether an application instance is healthy and ready to receive traffic.

Health checks protect users from failed or partially working servers.

---

## Why Health Checks Are Required
A server may be running but still unable to serve requests.

Examples:
- Web service not started
- Application files missing
- Permission issues
- Configuration errors

Health checks detect these conditions automatically.

---

## Load Balancer Health Checks
The Application Load Balancer performs regular health checks on backend instances.

It sends HTTP requests to a predefined path and expects a successful response.

Only healthy instances receive user traffic.

---

## Health Check Path
The health check path used is:



Reasons for choosing this path:
- Always available
- Stateless
- Fast to respond
- Does not require authentication

A successful `200 OK` response marks the instance as healthy.

---

## Health Check Frequency and Impact
Health checks are performed periodically.

If an instance fails multiple consecutive checks:
- It is marked unhealthy
- Traffic is stopped immediately
- The instance is removed from rotation

This prevents users from reaching broken servers.

---

## Integration With Auto Scaling
Auto Scaling Groups use health check results to maintain capacity.

If an instance remains unhealthy:
- It is terminated automatically
- A new instance is launched
- User Data configures the replacement
- Health checks validate readiness

This enables automatic recovery.

---

## Failure Behavior Observed
During failure simulations:
- Instances failed health checks after termination
- Traffic was rerouted to healthy instances
- Replacement instances passed health checks
- Service availability was restored automatically

This confirms correct health check behavior.

---

## Engineering Outcome
By using health checks:
- Users are protected from failures
- Broken servers are isolated
- Recovery is automated
- System behavior remains predictable

Health checks are essential for reliable operations.
