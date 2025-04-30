
# Project Plan - FrogPad - Applet Clean Deployment on FrogPad - 2025-04-29

---

## 🌍 Project Title
Deploy Applet Server on a New FrogPad Droplet (for PostgreSQL UI Management)

---

## 🌟 Project Objective
- Deploy a clean, dedicated Applet server into the FrogPad VPC.
- Securely connect to internal PostgreSQL database.
- Build and test a basic UI dashboard to manage research session data.
- Maintain maximum stability, isolation, and growth potential.

---

## 📋 Project Scope
| Item | Included? |
|:-----|:---------|
| New Droplet Creation | ✅ |
| Docker + Docker Compose Installation | ✅ |
| Applet Deployment (via Docker Compose) | ✅ |
| Private Database Connection to PostgreSQL | ✅ |
| Basic Test Page (Database Viewer) | ✅ |
| Public Access (HTTPS/Domain Setup) | ❌ (Deferred until private test successful) |
| SSL Setup | ❌ (Deferred until needed) |

---

## 🔠 Key Decisions (Confirmed)
| Area | Decision |
|:-----|:---------|
| Droplet Name | `applet.frogpad.ai` |
| Region | NYC3 |
| VPC | `frogpad-vpc` |
| Specs | 2 GB RAM / 1 vCPU / 50 GB SSD |
| Access Control | Private IP for PostgreSQL only |
| Deployment Method | Official Appsmith Docker Compose |
| Protocol | Slow, session-driven buildout |

---

## 🧩 Major Project Steps

| Step | Description |
|:-----|:------------|
| Step 1 | Create new droplet inside `frogpad-vpc` |
| Step 2 | Install Docker and Docker Compose on the new droplet |
| Step 3 | Pull and configure Appsmith official Docker Compose setup |
| Step 4 | Launch Applet server internally on port 8080 |
| Step 5 | Connect Applet to FrogPad PostgreSQL |
| Step 6 | Build first UI page: Database Table Viewer |
| Step 7 | Review performance, logs, and stability |
| Step 8 | (Optional) Prepare for public domain + SSL if needed later |

---

## 🔄 Protocol Alignment
- One actionable step at a time
- Confirmations required between steps
- Strict adherence to file naming conventions
- Markdown `.md` files for all planning and reporting artifacts
- Smooth, methodical pace: "Slow is smooth, smooth is fast"

---

## 📅 Date
April 29, 2025
