# 🛡️ Cloud-Based Malware Scanner API  
### ✨ Powered by YARA, ClamAV, and Azure Serverless Magic

Welcome to the future of automated malware detection and sandboxing — built entirely in the cloud.  
This project combines real-time threat detection, behavioral analysis, and secure execution into a **serverless, scalable malware scanning API**.  

---

## 🚀 What It Does

🔍 **Scans uploaded files** for malware  
🧠 **Analyzes file hashes** with custom YARA rules  
🧬 **Identifies malware family** and potential behavior  
💣 **Executes suspicious files** in an isolated Azure Container sandbox  
📄 **Generates detailed scan reports** and pushes them to cloud storage

It doesn’t just say *“infected.”*  
It tells you *what the threat is*, *what it could do*, and then *executes it safely in a sandbox* to observe behavior.

---

## 🧠 Key Components

### 🧬 YARA Rules Engine
- Hashes every uploaded file
- Matches against threat intel rules
- Identifies known malware signatures & behavior
- Classifies threats (e.g., Trojan, Infostealer, Ransomware)

### 💥 ClamAV Sandbox (ACI)
- Suspicious files are detonated in a fresh Azure Container Instance
- Uses ClamAV for signature scanning
- Logs runtime behavior in a secure, isolated environment
- Fully destroyed after each run

---

## 🧩 Tech Stack

- **Microsoft Azure** (Blob Storage, File Share, Functions, ACI)
- **ClamAV** (Open-source antivirus)
- **YARA** (Pattern-matching engine for malware rules)
- **Python / PowerShell** (automation & orchestration)
- **Serverless-first architecture** — no VMs, no overhead

---

## 📦 How It Works

1. A file is uploaded to Azure Blob Storage (`uploads/`)
2. An Azure Function is triggered automatically
3. File hash is calculated → YARA rules are applied
4. If malicious, the file is copied to Azure File Share
5. An Azure Container Instance is launched
6. File is scanned and executed securely
7. A plain-text or JSON report is uploaded to `report/` Blob Storage

---

## 💡 Why This Matters

✅ Built for modern cloud security workflows  
✅ No VMs, no patching, no headaches  
✅ Fast, scalable, cost-efficient  
✅ Ideal for CI/CD pipelines, secure upload APIs, or threat research

---

## 📁 Output Example

```json
{
  "filename": "invoice.exe",
  "clamav_result": "FOUND: Win.Trojan.Agent",
  "yara_match": "STEALER_GEN_05",
  "sandbox_behavior": ["keylogging", "network beaconing"],
  "verdict": "HIGH RISK",
  "report_path": "https://<storage>/report/invoice.txt"
}

---

## 📦 General Architechture

![Project Logo](images/logo.png)

