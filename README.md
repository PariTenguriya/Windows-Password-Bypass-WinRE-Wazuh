# Windows Password Bypass Lab — WinRE & Utilman.exe

## Overview

This project demonstrates a Windows security lab involving abuse of the
Windows Recovery Environment (WinRE) and the Accessibility Features mechanism.

The lab covers both offensive and defensive perspectives:

- WinRE-based system file modification
- Utilman.exe accessibility-feature abuse
- Pre-authentication SYSTEM execution
- Windows event monitoring
- Wazuh SIEM detection
- File Integrity Monitoring (FIM)
- Forensic investigation
- System restoration
- Defensive hardening

> ⚠️ This project was performed strictly in an authorized educational
> lab environment. Do not perform these techniques on systems without
> explicit authorization.

## MITRE ATT&CK

| Technique | ID |
|---|---|
| Accessibility Features | T1546.008 |

## Lab Environment

- Windows 10 / Windows 11
- Windows Recovery Environment (WinRE)
- CMD
- Wazuh SIEM
- Wazuh File Integrity Monitoring
- VMware / Virtual Machine environment

## Attack Overview

The lab demonstrates how physical or console access to an unencrypted
Windows installation can allow modification of accessibility binaries
through WinRE.

The modified accessibility executable can then be triggered from the
Windows login screen before normal authentication.

This results in SYSTEM-level command execution.

## Detection

Wazuh was used to monitor the Windows endpoint and identify suspicious
activity associated with:

- System32 file modification
- Suspicious process creation
- Accessibility binary modification
- Windows security events
- Potential privileged account creation

Important Windows events investigated include:

- Event ID 4663 — File Access
- Event ID 4670 — Permissions Changed
- Event ID 4656 — Object Handle Requested
- Event ID 4688 — Process Creation
- Event ID 4732 — Privileged Group Membership Change

## Wazuh FIM

The lab demonstrates monitoring of critical Windows System32 binaries
using Wazuh File Integrity Monitoring.

Particular attention was given to accessibility-related binaries such as:

- utilman.exe
- sethc.exe
- osk.exe
- narrator.exe
- magnify.exe

## Investigation

Forensic checks included:

- SHA256 hash comparison
- File metadata analysis
- Detection of suspicious backup files
- Windows Security Event Log analysis
- Process-parent investigation
- Local administrator account investigation

## Remediation

After testing, the modified system binary was restored to its original
state.

The lab also evaluated defensive controls including:

- BitLocker
- UEFI Secure Boot
- BIOS/UEFI password
- Windows Defender Credential Guard
- Wazuh FIM
- AppLocker / WDAC
- WinRE security controls

## Key Learning Outcomes

This project demonstrates practical understanding of:

- Windows privilege escalation concepts
- Pre-authentication attack surfaces
- Physical access threats
- Windows internals
- MITRE ATT&CK mapping
- SIEM monitoring
- File Integrity Monitoring
- Security event analysis
- Incident investigation
- Endpoint hardening

## Disclaimer

This repository is intended solely for cybersecurity education,
authorized penetration testing, defensive research, and isolated lab use.

Do not use these techniques against systems without explicit permission.
