# ForensicBackupScan.ps1

![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-blue?logo=powershell)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey?logo=windows)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Stable-success)

## 📌 Overview

**ForensicBackupScan.ps1** is an advanced Windows PowerShell script for conducting **forensic-level backup and access scans**. It is designed for incident response, security audits, and digital forensics investigations.

The script identifies backup artifacts (visible, hidden, or with Alternate Data Streams), checks for installed backup/sync software, lists shadow copies, analyzes logons for unusual activity (including brute-force attempts), and extracts recent traces from AnyDesk and TeamViewer.

---

## ✨ Key Features

* **Backup Detection**

  * Scans for files with backup-related extensions and suspicious keywords
  * Detects hidden and system-marked backup files
  * Identifies Alternate Data Streams (ADS)
* **Software & Configuration Inspection**

  * Lists installed backup/sync/cloud applications from registry
  * Detects suspicious scheduled tasks and services
* **Logon Event Analysis**

  * Extracts successful, failed, and locked-out logons
  * Lists top remote IP addresses
  * Detects brute-force indicators (≥10 failed logins in ≤5 min)
* **Shadow Copy Enumeration**

  * Lists available shadow copies using `vssadmin`
* **Remote Access Traces**

  * Retrieves last 200 lines from AnyDesk and TeamViewer logs (if present)
* **Comprehensive Reporting**

  * CSV and TXT reports with clear structure
  * Timestamped output directory on Desktop

---

## 🛠 Requirements

* **OS:** Windows 10/11 or Windows Server 2016+
* **PowerShell:** Version 5.1+ or PowerShell Core
* **Privileges:** Must be run as Administrator
* **Execution Policy:**

  ```powershell
  Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
  ```

---

## 🚀 Usage

1. **Clone or Download** this repository.
2. Open **PowerShell as Administrator**.
3. Navigate to the script directory:

   ```powershell
   cd "C:\Path\To\Script"
   ```
4. Run the script with optional parameters:

   ```powershell
   .\ForensicBackupScan.ps1 -LookbackDays 14 -MinSizeMB 30 -Drives C:\,D:\ -TopNRecent 80
   ```

### Parameters

| Parameter       | Description                                                      |
| --------------- | ---------------------------------------------------------------- |
| `-LookbackDays` | Days back to scan event logs (default: 30)                       |
| `-MinSizeMB`    | Minimum file size in MB for backup candidates (default: 20)      |
| `-Drives`       | Drives to scan (default: C:, D:, E:)                             |
| `-TopNRecent`   | Number of most recent items to display in summary (default: 100) |

---

## 📂 Output Structure

When complete, the script creates a folder on the Desktop:

```
ForensicReport_YYYYMMDD_HHMMSS
```

Inside you’ll find:

| File                        | Description                                  |
| --------------------------- | -------------------------------------------- |
| `Report.txt`                | Main text summary of findings                |
| `backup_candidates.csv`     | Detected backup-like files                   |
| `hidden_suspicious.csv`     | Hidden/system backup-related files           |
| `ads_streams.csv`           | Alternate Data Streams found                 |
| `scheduled_tasks.csv`       | Scheduled tasks with suspicious keywords     |
| `services_suspect.csv`      | Services with suspicious keywords            |
| `logons_success.csv`        | Successful logon events                      |
| `logons_failed.csv`         | Failed logon events                          |
| `logons_lockouts.csv`       | Account lockout events                       |
| `bruteforce_indicators.csv` | Brute-force login patterns                   |
| `anydesk_tail.txt`          | Last 200 lines of AnyDesk logs (if found)    |
| `teamviewer_tail.txt`       | Last 200 lines of TeamViewer logs (if found) |

---

## 🔍 Example Output (Report.txt excerpt)

```
=== Forensic Backup & Access Scan ===
Date: 2025-08-05
Host: WIN10LAB | User: Admin
Drives: C:\, D:\
LookbackDays: 14 | MinSizeMB: 30
Output dir: C:\Users\Admin\Desktop\ForensicReport_20250805_103000
---------------------------------------------------------------------

[1] Scanning for backup-like files (including hidden/system)...
Found 32 candidate files. Top 5 most recent:
LastWriteTime        SizeMB Attributes FullName
-------------        ------ ---------- --------
2025-08-04 23:15:10  250.34 Archive    C:\Backup\full_backup_2025.zip
...

[7] Logon analysis (Security log) since 7/22/2025 ...
Top failed IPs:
Count Name
----- ----
15    192.168.1.45
12    185.33.55.22
...
```

---

## ⚠️ Disclaimer

This tool is intended for **authorized forensic and security assessments** only.
Running it without consent may violate laws or regulations.
Use responsibly.

---

## 📜 License

[MIT License](LICENSE)
