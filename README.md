# SOC-Defender-Configuration-Change-Investigation
## Overview

This lab demonstrates how a SOC analyst investigates Microsoft Defender configuration changes using **Windows Defender Operational Event ID 5007**.

Rather than simply changing Defender settings, the focus is on identifying configuration modifications, validating whether they were expected, building an investigation timeline, and determining whether the activity represents legitimate administration or potential defense evasion.

---

## Lab Objectives

- Verify Microsoft Defender health
- Review current Defender configuration
- Modify a Defender configuration setting
- Investigate Event ID 5007
- Validate changes using PowerShell
- Correlate Event Viewer and PowerShell evidence
- Build an investigation timeline
- Restore the original configuration
- Map findings to MITRE ATT&CK

---

## Lab Environment

- Windows 10 VM
- Microsoft Defender Antivirus
- Windows Security
- Windows Event Viewer
- Windows PowerShell

---

## Tools Used

- Microsoft Defender Antivirus
- Windows Event Viewer
- PowerShell
- Windows Defender Operational Log

---

## Commands Used

Verify Defender Health

```powershell
Get-MpComputerStatus
```

Review Defender Configuration

```powershell
Get-MpPreference
```

Example Configuration Change

```powershell
Set-MpPreference -PUAProtection Enabled
```

Review Defender Operational Log

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Windows Defender/Operational" -MaxEvents 30
```

Restore Configuration

```powershell
Set-MpPreference -PUAProtection Disabled
```

---

## Investigation Summary

During the lab:

- Microsoft Defender health was verified.
- A Defender configuration setting was modified.
- Windows Defender generated Event ID 5007.
- Event Viewer recorded the configuration change.
- PowerShell confirmed the change.
- The change was analyzed from a SOC analyst perspective.
- Original configuration was restored.

---

# MITRE ATT&CK Mapping

| Technique | Description |
|-----------|-------------|
| T1562.001 | Impair Defenses – Disable or Modify Security Tools |
| T1112 | Modify Registry |
| T1059.001 | PowerShell |
| T1082 | System Information Discovery |

---

## Event IDs Investigated

| Event ID | Description |
|----------|-------------|
| 5007 | Microsoft Defender configuration changed |

---

## Skills Demonstrated

- Microsoft Defender
- Windows Security
- Windows Event Viewer
- Event ID 5007 Investigation
- PowerShell
- Windows Endpoint Security
- SOC Investigation
- Timeline Analysis
- Detection Validation
- MITRE ATT&CK Mapping
