# eyewitness-kali-fix-2025
Fixing EyeWitness 0.36.0 for Kali Linux (May 2025) and replacing GoWitness

# EyeWitness v0.36.0 Integration into Recon Workflow (Kali Linux, May 2025)

![MIT License](https://img.shields.io/badge/license-MIT-green)
![Kali Linux](https://img.shields.io/badge/Platform-Kali%20Linux-blue)
![EyeWitness](https://img.shields.io/badge/EyeWitness-v0.36.0-purple)
![Maintained](https://img.shields.io/badge/Status-Maintained-brightgreen)


This repository documents my process of **replacing Gowitness** with the **latest EyeWitness v0.36.0** in my `recon.sh` script on Kali Linux, as part of hands-on penetration testing practice (inspired by the TCM PNPT course).

---

## ✅ Summary

On May 4, 2025, I spent the day debugging and adapting my recon script to:

- Install and configure EyeWitness v0.36.0 on Kali
- Replace Gowitness in my recon.sh automation
- Solve Python dependency issues
- Manually compile geckodriver and fix PATH errors
- Make the screenshots + report generation work cleanly again

---

## ⚙️ Tech Stack & Versions

| Tool             | Version     | Notes |
|------------------|-------------|-------|
| EyeWitness       | 0.36.0      | Manual install from Red Siege repo (Python version) |
| Kali Linux       | 2024.4+     | Tilix terminal, zsh shell |
| Python           | 3.11.x      | Virtual environment used |
| selenium         | 3.141.0     | Needed for compatibility |
| urllib3          | 1.26.16     | Compatibility with selenium 3.x |
| geckodriver      | 0.36.0      | Downloaded and placed in `/usr/local/bin` manually |
| recon.sh         | custom      | Replaced gowitness with working EyeWitness setup |

---

## 🔁 Changes Made to recon.sh

Here’s what I changed:

```bash
# OLD gowitness command
gowitness file -f "$subdomain_path/alive.txt" --screenshot-path "$screenshot_path"

# NEW EyeWitness command (inside /EyeWitness/Python folder)
cd ~/EyeWitness/Python
python3 EyeWitness.py --web -f "$subdomain_path/alive.txt" -d "$base_dir/output"
