# 🔐 SIEM Detection Engineering & Log Pipeline Design

## 🔹 Overview
Designed and implemented a **security monitoring architecture** to improve detection visibility, log coverage, and incident response readiness across enterprise infrastructure.

Goal:
> Move from "logs exist" → to → "actionable security detection"

---

## 🔹 Problem Statement

The environment had multiple security tools (firewalls, VPN, IAM, servers), but:

- Logs were not centralized  
- No standardized log format or correlation  
- Detection use-cases were missing or incomplete  
- High noise, low signal (alert fatigue)  
- Limited visibility into user behavior  

**Impact:**
- Security incidents could go undetected  
- SOC lacked actionable insights  

---

## 🔹 Objectives

- Design centralized SIEM architecture  
- Build log ingestion pipeline  
- Create high-value detection use-cases  
- Reduce noise and improve signal quality  
- Enable incident response visibility  

---

## 🔹 Architecture Design

### Design Principles

- Collect logs from critical control points  
- Normalize → Correlate → Detect  
- Focus on identity + access behavior  
- Ensure logs are actionable  

---

## 🔹 SIEM Architecture Diagram

```mermaid
flowchart TD

%% Log Sources
A[Firewalls<br/>Palo Alto / Check Point] --> L[Log Collectors]
B[VPN Gateways<br/>IPSEC / SSL VPN] --> L
C[IAM / AAA<br/>Cisco ISE / AD] --> L
D[Servers / OS Logs] --> L
E[Cloud Logs<br/>AWS CloudTrail] --> L

%% Pipeline
L --> P[Log Processing Layer<br/>Parsing / Normalization]
P --> S[SIEM Platform<br/>Splunk / Sumo Logic]

%% Detection
S --> D1[Correlation Rules]
S --> D2[Detection Use Cases]
S --> D3[Dashboards]

%% Response
D1 --> R[Security Alerts]
D2 --> R
R --> SOC[Security Operations Team]

%% Feedback loop
SOC -->|Tuning / Feedback| D1
```
---

## 🔹 Log Pipeline Design
### Log Sources
- Firewalls (traffic, threat logs)
- VPN (user login, session activity)
- IAM / AAA (authentication, authorization)
- Windows/Linux systems
- Cloud logs (AWS)

---

### Processing Flow
1.Collection
- Syslog / API ingestion
2.Parsing
- Normalize fields (user, IP, action, timestamp)
3.Enrichment
- Geo-location
- User identity
- Asset criticality
4.Indexing
- Structured storage in SIEM
