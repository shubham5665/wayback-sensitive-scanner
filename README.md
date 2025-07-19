# 🔎 Wayback Sensitive Param Scanner v3.0

A powerful Python CLI tool that fetches historical URLs from the [Wayback Machine](https://archive.org/web/) and scans for:

- ✅ **Sensitive parameters** in query strings (e.g., `?password=`, `?token=`, `?apikey=`)
- ✅ **Sensitive keywords** in URL paths or filenames (e.g., `/admin`, `/backup.zip`, `.pdf`, `.docx`)

Perfect for **bug bounty recon**, **red teaming**, or general **security research**.

---

## 🚀 Features

- 📤 Collects URLs using Wayback CDX API
- 🔐 Detects over 30+ sensitive parameters
- 🛠️ Path-based keyword matching (e.g., `/admin`, `/config`)
- 🌈 Color-coded, user-friendly CLI output
- 💨 Fast, minimal & no dependencies other than `requests` and `termcolor`

---

## 📥 Installation

```bash
git clone https://github.com/shubham5665/wayback-sensitive-scanner.git
cd wayback-sensitive-scanner
pip install -r requirements.txt
