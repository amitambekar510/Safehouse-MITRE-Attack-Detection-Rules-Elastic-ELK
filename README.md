# 🛡️ Elastic-Detection-Rules — MITRE ATT&CK® Coverage

<div align="center">

![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-v15-red?style=for-the-badge&logo=mitre&logoColor=white)
![Elastic SIEM](https://img.shields.io/badge/Elastic%20SIEM-8.x%20%7C%209.x-005571?style=for-the-badge&logo=elastic&logoColor=white)
![Rules](https://img.shields.io/badge/Detection%20Rules-54%20TOML-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-Elastic%20License%20v2-blue?style=for-the-badge)
![Maintained](https://img.shields.io/badge/Maintained-Yes-success?style=for-the-badge)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20Cloud-orange?style=for-the-badge)

**Production-grade Elastic Security detection rules mapped to every MITRE ATT&CK® tactic,**
**covering Windows, Linux, Cloud, and Firewall data sources — including advanced UEBA rules.**

*Author: Amit Ambekar / Safehouse*

</div>

---

## 📌 Overview

This repository contains **54 production-ready Elastic Security detection rules** authored in the
native Elastic `.toml` format, directly importable into **Elastic SIEM / Elastic Security 8.x+**.
Rules are fully mapped to the **MITRE ATT&CK® Enterprise Framework v15** and cover all 14 tactics
— from Reconnaissance through to Impact — plus a dedicated **UEBA (User and Entity Behavior
Analytics)** rule set for Windows endpoints, Linux servers, and perimeter firewalls.

Every rule includes:
- ✅ Full MITRE ATT&CK technique + sub-technique mapping
- ✅ EQL (Event Query Language) detection logic
- ✅ Risk score, severity, and tag classification
- ✅ Triage, investigation steps, and remediation notes
- ✅ False positive analysis
- ✅ Data source index pattern mapping

---

## 🗂️ Repository Structure

```
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
```

---

## 📋 Rule Coverage Matrix

### MITRE ATT&CK® Tactic Coverage

| # | Tactic | ID | Rules | Key Techniques |
|---|--------|----|-------|----------------|
| 1 | Reconnaissance | TA0043 | 2 | T1595 Active Scanning, T1598 Phishing for Info |
| 2 | Resource Development | TA0042 | 2 | T1583 Acquire Infrastructure, T1608 Stage Capabilities |
| 3 | Initial Access | TA0001 | 3 | T1566 Phishing, T1190 Exploit Public-Facing App, T1078 Valid Accounts |
| 4 | Execution | TA0002 | 4 | T1059 Script Interpreter, T1047 WMI, T1053 Scheduled Task |
| 5 | Persistence | TA0003 | 6 | T1547 Registry Run Keys, T1543 Services, T1197 BITS Jobs, T1137 Office Add-ins, T1546 WMI Sub, T1574 DLL Hijack |
| 6 | Privilege Escalation | TA0004 | 3 | T1548 UAC Bypass, T1134 Token Impersonation, T1068 Kernel Exploit |
| 7 | Defense Evasion | TA0005 | 6 | T1055 Process Injection, T1562 Impair Defenses, T1036 Masquerading, T1070 Indicator Removal, T1497 Sandbox Evasion, T1553 Trust Controls |
| 8 | Credential Access | TA0006 | 4 | T1003 LSASS Dump, T1558 Kerberoasting, T1555 Browser Creds, T1111 MFA Fatigue |
| 9 | Discovery | TA0007 | 3 | T1087 Account Discovery, T1580 Cloud Discovery, T1083 File Discovery |
| 10 | Lateral Movement | TA0008 | 3 | T1021 SMB/RDP, T1550 Pass-the-Hash, T1210 Remote Exploit |
| 11 | Collection | TA0009 | 2 | T1113 Screen Capture, T1039 Network Share, T1119 Auto Collection |
| 12 | Command & Control | TA0011 | 3 | T1071 App Layer Protocol, T1105 Ingress Tool Transfer, T1571 Non-Standard Port |
| 13 | Exfiltration | TA0010 | 2 | T1041 C2 Exfil, T1048 Alt Protocol, T1567 Web Service |
| 14 | Impact | TA0040 | 3 | T1490 Inhibit Recovery, T1486 Ransomware, T1496 Cryptomining |

### UEBA Behavioral Rules

| Platform | Rules | Behaviors Detected |
|----------|-------|--------------------|
| **Windows** | 3 | Impossible travel logon, off-hours admin, admin tool abuse by std user, account lifecycle anomaly |
| **Linux** | 3 | Sudo abuse, cron injection, SSH root login, service shell spawn, reverse shell, SUID creation, container escape |
| **Firewall** | 2 | East-West port scan, geo-impossible flows, C2 beaconing, DGA detection, firewall rule tampering |

---

## 🔍 Highlighted Rules

| Rule File | Severity | Technique | Description |
|-----------|----------|-----------|-------------|
| `credential_access_lsass_memory_dump.toml` | 🔴 Critical | T1003.001 | Mimikatz, ProcDump, comsvcs MiniDump, Task Manager LSASS access |
| `impact_ransomware_shadow_copy_deletion.toml` | 🔴 Critical | T1490 | VSS delete, BCDEdit recovery disable, wbadmin catalog deletion |
| `credential_access_kerberoasting_dcsync.toml` | 🔴 Critical | T1558.003, T1003.006 | Kerberoasting RC4, AS-REP Roasting, DCSync replication rights |
| `lateral_movement_pth_psexec_smb.toml` | 🔴 Critical | T1550.002 | Pass-the-Hash NTLM, PsExec service creation, SMB admin shares |
| `ueba_linux_kernel_exploit_container_escape.toml` | 🔴 Critical | T1611 | Docker socket access, nsenter, /etc/ld.so.preload rootkit, setcap |
| `defense_evasion_av_edr_disable_amsi_bypass.toml` | 🔴 High | T1562.001 | Windows Defender disable, AMSI patching, Tamper Protection off |
| `privesc_token_impersonation_potato_attack.toml` | 🔴 High | T1134.001 | JuicyPotato, RoguePotato, GodPotato, PrintSpoofer |
| `ueba_firewall_longconn_dga_rule_tamper.toml` | 🔴 High | T1568.002 | DGA domain detection, long-lived C2 sessions, firewall rule bypass |

---

## ⚙️ Requirements

| Component | Version |
|-----------|---------|
| Elastic Security / SIEM | 8.0+ (recommended 8.12+) |
| Elastic Agent / Beats | 8.x |
| EQL Engine | Included with Elastic Security 8.x |
| Data Sources | Elastic Defend, Sysmon, Windows Event Logs, Network/Packetbeat |

### Required Elastic Integrations (by rule category)

- **Endpoint:** `elastic_agent` with Elastic Defend policy
- **Windows:** `winlogbeat` or `windows` integration (Security Event Logs, Sysmon)
- **Linux:** `system` integration (`logs-system.auth-*`, `logs-system.syslog-*`)
- **Network:** `network_traffic` / Packetbeat or firewall log integrations
- **Cloud:** `aws`, `azure`, `okta`, `google_workspace`, `o365` integrations

---

## 🚀 Installation & Import

### Method 1 — Kibana UI (Recommended)

```
Elastic Security → Rules → Detection Rules → Import Rules → Upload .toml
```

Select all `.toml` files from the desired category folder and import.

---

## 📐 Rule Schema Reference

Each `.toml` rule follows the standard Elastic detection rule schema:

```toml
[metadata]
creation_date = "2026/04/01"
updated_date  = "2026/05/04"
maturity      = "production"

[rule]
author        = ["Amit Ambekar / Safehouse"]
name          = "Rule Name"
description   = "Detailed description..."
type          = "eql"                    # eql | query | threshold | ml | new_terms
language      = "eql"
index         = ["logs-endpoint.events.*"]
query         = '''EQL query here'''
risk_score    = 73                       # 0–100
severity      = "high"                  # low | medium | high | critical
from          = "now-9m"
license       = "Elastic License v2"
tags          = ["Tactic: ...", "Data Source: ..."]

[[rule.threat]]
framework     = "MITRE ATT&CK"

[[rule.threat.technique]]
id            = "T1003"
name          = "OS Credential Dumping"
reference     = "https://attack.mitre.org/techniques/T1003/"

[rule.threat.tactic]
id            = "TA0006"
name          = "Credential Access"
reference     = "https://attack.mitre.org/tactics/TA0006/"
```

---

## 🧠 Data Sources Covered

```
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
```

---

## 🎯 UEBA — Behavioral Analytics Details

The `ueba/` folder contains **pure behavioral baseline rules** that go beyond signature detection:

### Windows UEBA
| Rule | Detects |
|------|---------|
| `ueba_windows_impossible_travel_offhours_admin.toml` | Logon from geographically impossible source, service account interactive logon, off-hours privileged activity |
| `ueba_windows_admin_tool_abuse_by_standard_user.toml` | Standard user running 4+ admin/recon tools in 5 min followed by lateral movement attempt |
| `ueba_windows_account_lifecycle_anomaly.toml` | New admin account creation, unauthorized group membership change, dormant account reuse |

### Linux UEBA
| Rule | Detects |
|------|---------|
| `ueba_linux_sudo_cron_ssh_shell_anomaly.toml` | Sudo to root shell by app user, cron job modification, SSH root login, shell from web/DB process |
| `ueba_linux_reverse_shell_suid_outbound_staging.toml` | `bash -i >& /dev/tcp/`, nc/socat shell, SUID on /tmp binary, LD_PRELOAD injection |
| `ueba_linux_kernel_exploit_container_escape.toml` | Docker socket access from container, nsenter namespace escape, /etc/ld.so.preload rootkit, dangerous setcap |

### Firewall UEBA
| Rule | Detects |
|------|---------|
| `ueba_firewall_east_west_scan_geo_beacon_exfil.toml` | Internal port scan (East-West), connection to TOR ASNs, legacy protocol abuse, 100MB+ outbound |
| `ueba_firewall_longconn_dga_rule_tamper.toml` | Long-lived C2 sessions (>60 min), DGA NXDOMAIN burst, firewall config change by unauthorized user |

---

## 📊 Severity & Risk Score Guide

| Severity | Risk Score | Typical Use Case |
|----------|-----------|-----------------|
| 🔴 Critical | 90–100 | Ransomware, LSASS dump, DCSync, active lateral movement |
| 🟠 High | 70–89 | UAC bypass, credential theft, C2 communication, webshell |
| 🟡 Medium | 40–69 | Suspicious recon, BITS abuse, off-hours access |
| 🟢 Low | 1–39 | Informational, policy violations, baseline deviations |

---

## 📚 References & Resources

- [MITRE ATT&CK® Enterprise Matrix](https://attack.mitre.org/matrices/enterprise/)
- [Elastic Security Detection Rules (Official)](https://github.com/elastic/detection-rules)
- [Elastic EQL Documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/eql.html)
- [Elastic Security Labs](https://www.elastic.co/security-labs/)
- [LOLBAS Project](https://lolbas-project.github.io/)
- [CISA Known Exploited Vulnerabilities](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
- [Elastic Detect Engine Blog](https://www.elastic.co/blog/tag/security)

---

## 👤 Author

**Amit Ambekar**
*SOC Team Lead | amitambekar510 | Safehouse*
**Linkedin:- https://www.linkedin.com/in/amitmilindambekar/**
---

## ⚖️ License

This project is licensed under the **Elastic License 2.0 (ELv2)**.

See [LICENSE](./LICENSE) for full terms.

> Rules marked with `license = "Elastic License v2"` in their metadata are subject to
> Elastic License 2.0 terms. You may use, modify, and distribute these rules for internal
> security monitoring. Commercial redistribution requires written permission.

---

<div align="center">

**If this repository helped you improve your detection coverage, please ⭐ star it!**

*Built with ❤️ for the Blue Team community*

</div>
