# ForensicBackupScan.ps1
<div align="center">
![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-blue?logo=powershell)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey?logo=windows)
![License](https://img.shields.io/badge/License-Authorized%20Use%20Only-orange)
![Status](https://img.shields.io/badge/Status-Stable-success)
</div>
## 📌 Overview

**ForensicBackupScan.ps1** is a Windows PowerShell script built for **authorized forensic scans** and **security investigations**. It helps you quickly spot backups, hidden files, remote access traces, and unusual logins so you can respond effectively.

We believe in working **ethically** and **positively**. Let’s stay on the right side of cybersecurity, keeping good intentions and good energy.

---

## ✨ Key Capabilities

* **Backup Detection**: Finds backup-like files (visible, hidden, or in Alternate Data Streams)
* **Software Inventory**: Lists installed backup/sync/cloud software
* **Shadow Copy Checks**: Detects and lists shadow copies
* **Logon Analysis**: Highlights unusual login activity and brute-force attempts
* **Remote Access Traces**: Extracts recent logs from AnyDesk and TeamViewer
* **Comprehensive Reports**: Generates organized CSV and TXT outputs on your Desktop

---

## 🛠 Requirements

* Windows 10/11 or Windows Server 2016+
* PowerShell 5.1+ or PowerShell Core
* Administrator privileges
* Execution Policy adjustment:

  ```powershell
  Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
  ```

---

## 🚀 Usage Instructions

1. Download or clone this repository.
2. Open PowerShell as Administrator.
3. Navigate to the script location:

   ```powershell
   cd "C:\Path\To\Script"
   ```
4. Run the script:

   ```powershell
   .\ForensicBackupScan.ps1 -LookbackDays 14 -MinSizeMB 30 -Drives C:\,D:\ -TopNRecent 80
   ```

**Parameters:**

| Name            | Description                                             |
| --------------- | ------------------------------------------------------- |
| `-LookbackDays` | Days back to review event logs (default: 30)            |
| `-MinSizeMB`    | Minimum file size for backup candidates (default: 20MB) |
| `-Drives`       | Drives to scan (default: C:, D:, E:)                    |
| `-TopNRecent`   | Number of most recent results in summary (default: 100) |

---

## 📂 Output Structure

The script creates a folder on your Desktop:

```
ForensicReport_YYYYMMDD_HHMMSS
```

Inside you will find:

* `Report.txt` – Main summary
* `backup_candidates.csv` – Backup files found
* `hidden_suspicious.csv` – Hidden/system suspicious files
* `ads_streams.csv` – Alternate Data Streams found
* `scheduled_tasks.csv` – Suspicious scheduled tasks
* `services_suspect.csv` – Suspicious services
* `logons_success.csv` – Successful logon events
* `logons_failed.csv` – Failed logon events
* `logons_lockouts.csv` – Account lockouts
* `bruteforce_indicators.csv` – Brute-force attempt patterns
* `anydesk_tail.txt` – Last 200 lines from AnyDesk logs
* `teamviewer_tail.txt` – Last 200 lines from TeamViewer logs

---

## 🔍 Example Report Snippet

```
=== Forensic Backup & Access Scan ===
Date: 2025-08-05
Host: WIN10LAB | User: Admin
Drives: C:\, D:\
LookbackDays: 14 | MinSizeMB: 30
Output dir: C:\Users\Admin\Desktop\ForensicReport_20250805_103000
...
Found 32 candidate files. Top 5 most recent:
2025-08-04 23:15:10  250.34MB  C:\Backup\full_backup_2025.zip
```

---

## ⚠️ Ethical Use Statement

Use this tool only when you have explicit permission. Keep your work clean, legal, and in the spirit of positive cybersecurity.

---

## 👤 Credits
Created by **Eliran Loai Deeb**
[LinkedIn Profile](https://www.linkedin.com/in/loai-deeb/)
