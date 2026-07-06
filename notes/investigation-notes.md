# Investigation Notes

## Scenario

A SOC analyst receives an alert indicating that Microsoft Defender generated **Event ID 5007**, showing that the Defender configuration was modified.

The analyst must determine whether the change is legitimate or an indicator of potential defense evasion.

---

# Initial Verification

Verified Microsoft Defender health.

Command

```powershell
Get-MpComputerStatus
```

Result

- Microsoft Defender running
- Antivirus enabled
- Real-Time Protection enabled

---

# Defender Configuration Review

Reviewed current Defender configuration.

Command

```powershell
Get-MpPreference
```

Recorded baseline Defender settings before making any changes.

---

# Configuration Change

A legitimate Defender configuration change was performed.

Example:

```
PUA Protection Enabled
```

or

```
Cloud Protection Enabled
```

The change was made using PowerShell.

---

# Event Viewer Investigation

Location

Applications and Services Logs

Microsoft

Windows

Windows Defender

Operational

---

Observed Event

Event ID

```
5007
```

Meaning

Microsoft Defender configuration has changed.

The event recorded:

- Previous value
- New value
- Registry path
- Timestamp

---

# PowerShell Validation

Command

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Windows Defender/Operational" -MaxEvents 30
```

Confirmed that Event ID 5007 was generated immediately after the configuration change.

---

# Investigation Timeline

1. Verified Defender health.
2. Reviewed Defender configuration.
3. Modified Defender configuration.
4. Event ID 5007 generated.
5. Reviewed Event Viewer.
6. Validated using PowerShell.
7. Restored original configuration.

---

# SOC Assessment

Observed Activity

Expected administrative configuration change.

Risk

Low

Reason

The change was intentionally performed by an administrator.

No evidence of malware or unauthorized Defender tampering was identified.

---

# MITRE ATT&CK Mapping

### T1562.001

Impair Defenses

Configuration changes to Defender may indicate attempts to weaken endpoint protection.

---

### T1112

Modify Registry

Defender settings are stored in registry-backed configuration and modifications may generate Event ID 5007.

---

### T1059.001

PowerShell

Configuration changes performed through PowerShell should be monitored.

---

# Conclusion

Event ID 5007 provides valuable visibility into Microsoft Defender configuration changes.

SOC analysts should correlate configuration changes with administrator activity, PowerShell execution, and endpoint context to distinguish legitimate administration from malicious defense evasion.
