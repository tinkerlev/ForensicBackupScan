# ForensicBackupScan.ps1

![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-blue?logo=powershell)
![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey?logo=windows)
![License](https://img.shields.io/badge/License-Authorized%20Use%20Only-orange)
![Status](https://img.shields.io/badge/Status-Stable-success)

## 📌 Overview

**ForensicBackupScan.ps1** is a Windows PowerShell script designed for **authorized forensic scans** and **security investigations**. It’s here to help you uncover backups, hidden files, remote access traces, and unusual logins — so you can act fast and stay safe.

We believe in keeping our work **ethical** and **positive** — let’s always stay on the right side, with good spirit and good intentions.

---

## ✨ What It Does

* **Finds Backup Files** – visible, hidden, or even with Alternate Data Streams (ADS)
* **Lists Installed Backup/Sync Software**
* **Checks for Shadow Copies**
* **Analyzes Logons** – highlights unusual activity and brute-force attempts
* **Extracts Remote Access Traces** – AnyDesk & TeamViewer logs
* **Generates Full Reports** – CSV and TXT, saved neatly to your Desktop

---

## 🛠 Requirements

* Windows 10/11 or Windows Server 2016+
* PowerShell 5.1+ or PowerShell Core
* Administrator rights
* Execution Policy:

  ```powershell
  Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
  ```

---

## 🚀 How to Use

1. Download or clone this repository.
2. Open PowerShell as Administrator.
3. Navigate to the script folder:

   ```powershell
   cd "C:\Path\To\Script"
   ```
4. Run it:

   ```powershell
   .\ForensicBackupScan.ps1 -LookbackDays 14 -MinSizeMB 30 -Drives C:\,D:\ -TopNRecent 80
   ```

**Parameters:**

| Name            | Purpose                                                   |
| --------------- | --------------------------------------------------------- |
| `-LookbackDays` | Days back to check event logs (default: 30)               |
| `-MinSizeMB`    | Minimum file size to consider (default: 20MB)             |
| `-Drives`       | Drives to scan (default: C:, D:, E:)                      |
| `-TopNRecent`   | How many recent results to show in summary (default: 100) |

---

## 📂 Output

Creates a folder on your Desktop like:

```
ForensicReport_YYYYMMDD_HHMMSS
```

Inside:

* `Report.txt` – Main summary
* `backup_candidates.csv` – Backup files found
* `hidden_suspicious.csv` – Hidden/system suspicious files
* `ads_streams.csv` – Alternate Data Streams
* `scheduled_tasks.csv` – Suspicious scheduled tasks
* `services_suspect.csv` – Suspicious services
* `logons_success.csv` – Successful logons
* `logons_failed.csv` – Failed logons
* `logons_lockouts.csv` – Lockouts
* `bruteforce_indicators.csv` – Brute-force patterns
* `anydesk_tail.txt` – Last AnyDesk log lines
* `teamviewer_tail.txt` – Last TeamViewer log lines

---

## 🔍 Example Output

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

## ⚠️ Stay Ethical

Use this tool **only** when you have proper permission. Keep it clean, keep it legal, and keep the good energy.

**Created by:** Eliran Loai Deeb
[LinkedIn](https://www.linkedin.com/in/loai-deeb/)
