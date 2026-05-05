🛡️ Elastic-Detection-Rules — MITRE ATT&CK® Coverage

<div align="center">
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-v15-red?style=for-the-badge&logo=mitre&logoColor=white)
![Elastic SIEM](https://img.shields.io/badge/Elastic%20SIEM-8.x%20%7C%209.x-005571?style=for-the-badge&logo=elastic&logoColor=white)
![Rules](https://img.shields.io/badge/Detection%20Rules-54%20TOML-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-Elastic%20License%20v2-blue?style=for-the-badge)
![Maintained](https://img.shields.io/badge/Maintained-Yes-success?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20Cloud-orange?style=for-the-badge)
Production-grade Elastic Security detection rules mapped to every MITRE ATT&CK® tactic,
covering Windows, Linux, Cloud, and Firewall data sources — including advanced UEBA rules.
Author: Amit Ambekar / Safehouse
</div>


📌 Overview
This repository contains 54 production-ready Elastic Security detection rules authored in the
native Elastic `.toml` format, directly importable into Elastic SIEM / Elastic Security 8.x+.
Rules are fully mapped to the MITRE ATT&CK® Enterprise Framework v15 and cover all 14 tactics
— from Reconnaissance through to Impact — plus a dedicated UEBA (User and Entity Behavior
Analytics) rule set for Windows endpoints, Linux servers, and perimeter firewalls.
Every rule includes:
✅ Full MITRE ATT&CK technique + sub-technique mapping
✅ EQL (Event Query Language) detection logic
✅ Risk score, severity, and tag classification
✅ Triage, investigation steps, and remediation notes
✅ False positive analysis
✅ Data source index pattern mapping

🗂️ Repository Structure

elastic-rules/
├── reconnaissance/               # TA0043 — 2 rules
├── resource_development/         # TA0042 — 2 rules
├── initial_access/               # TA0001 — 3 rules
├── execution/                    # TA0002 — 4 rules
├── persistence/                  # TA0003 — 6 rules
├── privilege_escalation/         # TA0004 — 3 rules
├── defense_evasion/              # TA0005 — 6 rules
├── credential_access/            # TA0006 — 4 rules
├── discovery/                    # TA0007 — 3 rules
├── lateral_movement/             # TA0008 — 3 rules
├── collection/                   # TA0009 — 2 rules
├── command_and_control/          # TA0011 — 3 rules
├── exfiltration/                 # TA0010 — 2 rules
├── impact/                       # TA0040 — 3 rules
└── ueba/
    ├── windows/                  # UEBA — 3 rules
    ├── linux/                    # UEBA — 3 rules
    └── firewall/                 # UEBA — 2 rules

⚙️ Requirements
Component	Version
Elastic Security / SIEM	8.0+ (recommended 8.12+)
Elastic Agent / Beats	8.x
EQL Engine	Included with Elastic Security 8.x
Data Sources	Elastic Defend, Sysmon, Windows Event Logs, Network/Packetbeat
Required Elastic Integrations (by rule category)
Endpoint: `elastic_agent` with Elastic Defend policy
Windows: `winlogbeat` or `windows` integration (Security Event Logs, Sysmon)
Linux: `system` integration (`logs-system.auth-*`, `logs-system.syslog-*`)
Network: `network_traffic` / Packetbeat or firewall log integrations
Cloud: `aws`, `azure`, `okta`, `google_workspace`, `o365` integrations

🚀 Installation & Import
Method 1 — Kibana UI (Recommended)

Elastic Security → Rules → Detection Rules → Import Rules → Upload .toml
Select all `.toml` files from the desired category folder and import.

🧠 Data Sources Covered

Windows
├── Elastic Defend (EDR)         → logs-endpoint.events.*
├── Sysmon (Microsoft)           → logs-windows.sysmon_operational-*
├── Windows Security Event Log   → winlogbeat-* / logs-windows.forwarded*
└── PowerShell Logs              → logs-windows.powershell*

Linux
├── Elastic Defend (EDR)         → logs-endpoint.events.*
├── System Auth Logs             → logs-system.auth-*
└── Syslog                       → logs-system.syslog-*

Network / Firewall
├── Packetbeat / Network         → logs-network.* / packetbeat-*
├── Palo Alto Networks           → logs-panw.*
└── Fortinet FortiGate           → logs-fortinet.*

Cloud
├── Microsoft 365 / Azure AD     → logs-o365.* / logs-azure.*
├── Okta                         → logs-okta.*
└── AWS / GCP                    → logs-aws.* / logs-gcp.*

📊 Severity & Risk Score Guide

🔴 Critical	→ 90–100	→ Ransomware, LSASS dump, DCSync, active lateral movement
🟠 High →	70–89	→ UAC bypass, credential theft, C2 communication, webshell
🟡 Medium	 → 40–69	→ Suspicious recon, BITS abuse, off-hours access
🟢 Low	→ 1–39	→ Informational, policy violations, baseline deviations

📚 References & Resources
MITRE ATT&CK® Enterprise Matrix
Elastic Security Detection Rules (Official)
Elastic EQL Documentation
Elastic Security Labs
LOLBAS Project
CISA Known Exploited Vulnerabilities
Elastic Detect Engine Blog

👤 Author
Amit Ambekar | SOC Team Lead | amitambekar510 | Safehouse
Linkedin:- https://www.linkedin.com/in/amitmilindambekar/

If this repository helped you improve your detection coverage, please ⭐ star it!
Built with ❤️ for the Blue Team community
