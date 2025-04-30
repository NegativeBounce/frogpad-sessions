
# Session Report - FrogPad - Session 2.1.2 - Applet Deploy - 2025-04-29

---

## 🛡️ Session Title
UFW Firewall Installation and Configuration - applet.frogpad.ai

---

## 🎯 Objective
Install and configure a basic firewall (UFW) to secure the droplet before Docker installation.

---

## 📋 Actions Performed

| Task | Status |
|:-----|:-------|
| Install UFW | ✅ Completed |
| Allow OpenSSH (port 22) | ✅ Completed |
| Allow HTTP (port 80) | ✅ Completed |
| Allow HTTPS (port 443) | ✅ Completed |
| Enable UFW | ✅ Completed |
| Verify Firewall Status | ✅ Completed |

---

## 📋 Final Firewall Status

| Setting | Value |
|:--------|:------|
| Firewall | Active |
| Default Incoming | Deny |
| Default Outgoing | Allow |
| Logging | On (low) |
| Open Ports | 22/tcp (SSH), 80/tcp (HTTP), 443/tcp (HTTPS) |
| IPv6 Support | Enabled |

---

## 🔥 Observations
- Firewall is fully active and protecting the droplet.
- SSH, HTTP, and HTTPS ports are properly configured.
- Logging is enabled for audit purposes.
- Server is secure and clean, ready for next phase (Docker installation).

---

## ✅ Deliverables
- [x] UFW installed and active
- [x] Ports 22, 80, 443 allowed
- [x] Droplet surface secured before container deployment

---

## 📅 Date
April 29, 2025
