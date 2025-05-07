# 🧠 Session Report  
**Project:** CanvasAgentDashboard  
**Session:** 2.1 – Create and Configure Droplet  
**Date:** 2025-05-06  

---

## ✅ Tasks Completed

### 🖥️ Droplet Provisioned
- Name: `canvas.frogpad.ai`
- Region: NYC3
- Stack: 4 GB RAM / 2 vCPU / 80 GB SSD / Ubuntu 22.04
- VPC: `frogpad-vpc`
- Public IP: `167.71.99.88`
- Private IP: `10.108.16.13`

### ⚙️ System Setup
- Updated system packages
- Installed: `git`, `curl`, `ufw`, `fail2ban`
- Installed Node.js (v20+), npm, yarn

### 🔐 Firewall Configuration
- Allowed ports: `22`, `80`, `443`
- UFW enabled and active

### 🌐 SSL Setup
- Installed `nginx`, `certbot`
- Issued and configured SSL via Let's Encrypt
- HTTPS enforced for `canvas.frogpad.ai`

### 🔌 Tailscale VPN
- Tailscale installed and connected
- Tailscale IPv4: `100.111.100.75`
- SSH access via Tailscale enabled

---

## ⏱️ Duration Estimate
~45–60 minutes

---

## 🧠 Memory Reset Recovery Note
To resume:
> Begin with **Session 2.2: Clone GitHub Repo + Install Node Stack**

