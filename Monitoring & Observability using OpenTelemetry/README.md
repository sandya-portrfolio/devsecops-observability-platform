## Project Summary

Worked on implementing monitoring and observability solutions for banking and microservices-based applications to improve application performance, availability, and production issue troubleshooting. Integrated OpenTelemetry with monitoring tools to track real-time transactions, analyze failures, and identify root causes using logs, metrics, and traces. Supported distributed applications running on Kubernetes and ensured smooth communication between backend services such as authentication, payment, core banking, and notification systems.

---

## Tools Used

* OpenTelemetry
* Prometheus
* Grafana
* New Relic
* Kubernetes
* Docker
* Microservices Architecture
* Linux

---

## Roles & Responsibilities

* Implemented observability using OpenTelemetry for distributed microservices applications.
* Configured monitoring dashboards and alerts using Grafana and Prometheus.
* Monitored API health, transaction flows, server performance, and Kubernetes workloads.
* Analyzed logs, metrics, and traces to identify production issues and root causes.
* Troubleshot timeout issues, API failures, and backend service communication problems.
* Worked with DevOps and development teams during production incidents and deployments.
* Monitored resource utilization such as CPU, memory, and pod performance in Kubernetes clusters.
* Supported production environments and ensured application high availability.
* Investigated transaction failures in banking applications and verified backend service responses.
* Performed root cause analysis (RCA) for recurring production incidents.

---

# Major Issues & Answers

## Major issues faced in the project:

### 1. Payment Transaction Timeout Issues

**Issue:**
Users experienced transaction failures while transferring money due to delayed responses from backend payment services.

**Resolution:**
Used OpenTelemetry traces and logs to identify timeout points between payment and core banking services. Increased timeout handling and optimized backend API communication.

---

### 2. High API Error Rate

**Issue:**
API requests started failing during peak traffic hours.

**Resolution:**
Monitored error metrics in Grafana and Prometheus, identified overloaded services, and scaled Kubernetes pods to balance traffic.

---

### 3. Database Connectivity Failures

**Issue:**
Applications failed intermittently because services could not connect to the database.

**Resolution:**
Analyzed logs and traces to isolate DB connection issues, optimized connection pooling, and restarted affected database services.

---

### 4. Microservice Communication Failure

**Issue:**
Some services were unable to communicate with dependent backend services.

**Resolution:**
Verified service endpoints, checked Kubernetes networking, and resolved internal API routing issues.

---

### 5. High Resource Utilization

**Issue:**
CPU and memory usage increased unexpectedly, causing pod crashes.

**Resolution:**
Monitored Kubernetes resource metrics, optimized pod resource allocation, and enabled auto-scaling.

---

### 6. Application Downtime in Production

**Issue:**
Critical banking services became unavailable during production deployment.

**Resolution:**
Used monitoring alerts and observability dashboards to identify failing pods and performed rollback deployment to restore services quickly.

---

### 7. Delayed Notification Services

**Issue:**
Users received delayed transaction notifications after successful payments.

**Resolution:**
Traced request flow across notification services and fixed message queue processing delays.

---

### 8. Difficulty Identifying Root Cause of Failures

**Issue:**
Traditional monitoring showed failures but did not explain the actual cause.

**Resolution:**
Implemented observability using logs, metrics, and traces with OpenTelemetry to perform faster root cause analysis and proactive troubleshooting.
