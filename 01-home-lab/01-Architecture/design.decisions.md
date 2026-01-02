# Design Decisions – SOC Home Lab

This document explains the **architectural and technical decisions** behind the SOC Home Lab.  
The goal is to justify *why* each component exists and *how* it supports **SOC Analyst L1** and **BTL1**-aligned workflows.

## 1. Lab Objectives and Constraints

### Objectives
- Simulate a **realistic entry-level SOC environment**
- Practice **detection, investigation, and DFIR workflows**
- Use **industry-relevant tools** commonly seen in Blue Team roles
- Produce **clear, auditable documentation** suitable for a professional portfolio

### Constraints
- Single physical host
- Limited resources (CPU, RAM, disk)
- Fully isolated environment
- Reproducible and maintainable setup

These constraints influenced all architectural choices.


## 2. Hypervisor Selection

### VMware Workstation

**Why VMware Workstation:**
- Stable and mature virtualization platform
- Strong support for **custom network segments**
- Easy VM snapshot and rollback for incident scenarios
- Commonly used in professional and training environments

**SOC relevance:**
- Enables rapid restoration after malware execution
- Supports realistic multi-VM SOC environments


## 3. Network Architecture & Segmentation

### pfSense as Central Firewall

pfSense is used as the **core network control point**.

**Why pfSense:**
- Enterprise-grade firewall capabilities
- Clear interface separation (WAN / LAN / internal networks)
- Fine-grained traffic control
- Realistic SOC-style network topology

### Network Segments

The lab is divided into logical zones:

- **WAN** – simulated internet access
- **Internal LAN** – domain-joined endpoints
- **Management / SOC Network** – monitoring and analysis systems

**Benefits:**
- Enforces trust boundaries
- Allows realistic traffic inspection
- Enables log-centric visibility


## 4. Windows Domain Environment

### Windows Server 2019 – Active Directory

**Purpose:**
- Centralized authentication and authorization
- User, group, and computer management
- Generation of realistic Windows security events

**Why Active Directory is critical:**
- AD is a primary attack target in real environments
- Produces high-value logs for detection and investigation
- Essential knowledge for SOC Analysts

### Windows 10 Endpoints

**Purpose:**
- Simulate user activity
- Generate endpoint telemetry
- Act as targets for attack scenarios

**Configured with:**
- Sysmon
- Security auditing enabled
- Log forwarding to SIEM / EDR platforms


## 5. Linux Server Infrastructure

Linux servers are used to host **core SOC tooling**.

## 6. SIEM and Monitoring Strategy

### Splunk

**Role:**
- Centralized log aggregation
- Search-driven investigation
- Detection logic development

**Why Splunk:**
- Commonly used SIEM in SOC environments
- Strong correlation and query capabilities
- Frequently referenced in SOC job requirements


## 7. Network Visibility

### Zeek

**Role:**
- Network traffic analysis
- Protocol-level visibility
- Metadata-based detection

**Why Zeek:**
- SOC-friendly network telemetry
- Excellent for post-incident investigation
- Focuses on *what happened*, not just packets

### Wireshark

**Role:**
- Deep packet inspection
- Validation of suspicious traffic
- Evidence collection


## 8. DFIR Tooling Selection

The lab includes tools commonly used in **forensic investigations**.

### Disk & Artifact Analysis
- Autopsy
- FTK Imager
- KAPE

### Log & Event Analysis
- DeepBlueCLI
- Eric Zimmerman tools

**Why DFIR tooling is included:**
- BTL1 emphasizes investigation, not exploitation
- SOC Analysts must understand forensic artifacts
- Bridges detection with evidence-based response


## 9. Attacker / Analysis Machine

### Kali Linux / Kali Purple

**Purpose:**
- Generate controlled malicious activity
- Simulate attacker behavior
- Test detections and alerts

**Why Kali Purple:**
- Includes both offensive and defensive tooling
- Useful for purple-team style validation
- Controlled usage for detection testing only

