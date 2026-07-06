# Troubleshooting Notes

## Problem

Event ID 5007 does not appear.

### Solution

Wait 30–60 seconds after modifying Defender settings.

Refresh Event Viewer.

---

## Problem

PowerShell command fails.

### Solution

Run PowerShell as Administrator.

---

## Problem

Configuration does not change.

### Solution

Verify Microsoft Defender is running.

```powershell
Get-MpComputerStatus
```

Ensure:

- AntivirusEnabled = True
- RealTimeProtectionEnabled = True

---

## Problem

Unable to find Defender Operational log.

### Solution

Navigate to:

Applications and Services Logs

↓

Microsoft

↓

Windows

↓

Windows Defender

↓

Operational

---

## Problem

No Event ID 5007 found.

### Solution

Query recent Defender events using:

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Windows Defender/Operational" -MaxEvents 30
```

---

## Problem

Unable to restore original configuration.

### Solution

Run the corresponding `Set-MpPreference` command to return the modified setting to its original value.

Example:

```powershell
Set-MpPreference -PUAProtection Disabled
```

---

## Lessons Learned

- Event ID 5007 records Microsoft Defender configuration changes.
- Defender configuration changes should always be investigated.
- Correlating Event Viewer and PowerShell provides stronger evidence.
- Administrative changes and malicious defense evasion can generate similar events; context is essential.
- Monitoring Event ID 5007 helps SOC teams detect attempts to weaken endpoint security.
