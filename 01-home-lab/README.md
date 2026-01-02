# SOC Home Lab – Blue Team / BTL1 Preparation

This repository documents the design, deployment, and usage of a **SOC Home Lab** focused on an **SOC Analyst L1** role and **BTL1 (Blue Team Level 1)** exam preparation.

The lab simulates a realistic Security Operations Center environment to practice **detection, analysis, incident response, and DFIR** using common Blue Team tools.

## Lab Objectives

- Build a realistic **entry-level SOC environment**
- Practice day-to-day **SOC Analyst L1 workflows**
- Prepare for the **BTL1 certification**
- Create **documented, professional evidence** for a cybersecurity portfolio


## High-Level Architecture

- **Hypervisor:** VMware Workstation
- **Network segmentation:** pfSense
- **Windows domain:** Active Directory
- **Windows endpoints:** event generation and telemetry
- **Linux servers:** SIEM, EDR, and DFIR tooling
- **Attack / analysis machine:** Kali Linux

The architecture is designed to support:
- Legitimate and malicious traffic
- Centralized log collection
- Detection, investigation, and forensic analysis

## Operating Systems

- Windows Server 2019 (Domain Controller)
- Windows 10 (Workstations)
- Ubuntu Server (Splunk, Wazuh, MISP, etc.)
- Kali Linux / Kali Purple


## Core Tools

### Detection & Monitoring
- Splunk
- Wazuh
- Zeek
- Wireshark

### DFIR
- Autopsy
- FTK Imager
- KAPE
- DeepBlueCLI
- Eric Zimmerman Tools

### Supporting Tools
- CyberChef
- Sysmon

## SOC Workflows Practiced

- Log ingestion and normalization
- Detection of suspicious activity
- Event correlation and analysis
- Disk, memory, and log forensics
- Incident documentation and escalation notes

## Repository Contents

- Technical documentation of the lab
- Writeups of scenarios and exercises
- Cheatsheets and analyst notes
- Evidence and screenshots (when applicable)

## Professional Focus

This lab is built with a **real SOC mindset**, not as a CTF:
- Evidence-driven analysis
- Clear analyst reasoning
- Professional documentation
- SOC-ready terminology and structure

## Project Status

This is a **living project**.  
New scenarios, architectural improvements, and DFIR exercises will be added over time.


## 📎 Disclaimer

This lab is used **strictly for educational purposes** in controlled environments.
