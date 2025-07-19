# 🔎 Wayback Sensitive Param Scanner v3.0

A powerful Python CLI tool that fetches historical URLs from the [Wayback Machine](https://archive.org/web/) and scans for **sensitive parameters** and **keywords** in both query strings and URL paths.

Perfect for recon in bug bounty and red teaming engagements.

---

## 🎯 Features

- 🔍 Scans **Wayback Machine URLs** for sensitive query parameters
- 🛡️ Detects sensitive **keywords in paths or filenames** (e.g. `/admin`, `.pdf`, `/backup.zip`)
- ⚡ Fast & lightweight
- 🎨 Colorful CLI output

---

## 🛠️ Installation

```bash
git clone https://github.com/your-username/wayback-sensitive-scanner.git
cd wayback-sensitive-scanner
pip install -r requirements.txt
