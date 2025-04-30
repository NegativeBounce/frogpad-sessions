
# Session Report - FrogPad - Session 4.3 - Applet Deploy - 2025-04-29

---

## 🔐 Session Title
SSL Certificate Issuance via Certbot (Standalone Mode) – applet.frogpad.ai

---

## 🎯 Objective
Secure the Applet server with a valid SSL certificate issued by Let's Encrypt, using Certbot in standalone mode to avoid conflicts with Docker-managed Nginx.

---

## 📋 Actions Performed

| Task | Status |
|:-----|:-------|
| Stopped Appsmith containers to free up port 80 | ✅ Completed |
| Issued SSL certificate using Certbot in standalone mode | ✅ Completed |
| Restarted Appsmith containers after certificate issuance | ✅ Completed |
| Verified certificate path in `/etc/letsencrypt/live/applet.frogpad.ai/` | ✅ Completed |

---

## 📂 Certificate Files Issued

| File Type | Path |
|:----------|:-----|
| Full Chain | `/etc/letsencrypt/live/applet.frogpad.ai/fullchain.pem` |
| Private Key | `/etc/letsencrypt/live/applet.frogpad.ai/privkey.pem` |

---

## 🔥 Observations
- Certificate issuance was successful despite initial nginx plugin conflict.
- Standalone mode resolved the binding issue with Docker's embedded Nginx.
- Droplet is now ready for full HTTPS integration in Appsmith.

---

## ✅ Deliverables
- [x] Valid SSL cert installed
- [x] Let's Encrypt integration confirmed
- [x] Ready for SSL activation in Appsmith Docker environment

---

## 📅 Date
April 29, 2025
