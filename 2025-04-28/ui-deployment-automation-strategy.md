# ⚙️ UI Deployment Automation Strategy – Frogpad.AI

**Date**: 2025-04-21  
**Purpose**: Outline complete automation strategy for deploying UI frontend into Frogpad.AI ecosystem via GitHub → HTTPS deployment at `gateway.frogpad.ai`

---

## ✅ Goals of Automation

Automate the following tasks:

1. Clone or pull latest GitHub repo
2. Install project dependencies
3. Run production frontend build
4. Deploy build output to correct Nginx `root` folder
5. Configure or validate Nginx site file
6. Ensure HTTPS via Certbot (issue or renew SSL)
7. Reload Nginx server
8. (Optional) Generate and commit a Markdown session log to GitHub

---

## 🧱 Automation Options

### Option 1: GitHub Actions + SSH Deployment

**Trigger**: Push to `main` branch  
**Tool**: `appleboy/ssh-action`

**Sample GitHub Action:**
```yaml
name: Deploy UI to Gateway

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo
        uses: actions/checkout@v2

      - name: Build and deploy via SSH
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.GATEWAY_HOST }}
          username: root
          key: ${{ secrets.GATEWAY_SSH_KEY }}
          script: |
            cd /home/frogpad/apps/ui-gateway
            git pull origin main
            npm ci
            npm run build
            cp -r dist/* /var/www/frogpad-ui/
            nginx -t && systemctl reload nginx
```

---

### Option 2: n8n Workflow with AI Agent

- Triggered by webhook or UI
- SSH into droplet
- Execute steps via `Execute Command` nodes
- Optionally:
  - Write build logs to DB
  - Monitor SSL status
  - Trigger OpenAI summary or session log

---

### Option 3: Shell Script

**Command**: `./deploy-ui.sh`

**Script Contents**:
```bash
#!/bin/bash
cd /home/frogpad/apps/ui-gateway
git pull origin main
npm ci
npm run build

cp -r dist/* /var/www/frogpad-ui/

certbot renew --nginx
nginx -t && systemctl reload nginx
```

You can:
- Schedule it with `cron`
- Trigger manually
- Combine with `.md` log generator + Git push

---

## 🧩 Optional Enhancements

- Add health monitoring via Node.js or Nginx logs
- Push deployment summary to GitHub or Rocket.Chat
- Integrate version tagging into commit history
- Auto-snapshot database or proxy logs post-deploy

---

## 🧠 Memory Reset Recovery Note

> This file documents all automation strategies for UI deployment to `gateway.frogpad.ai`. Choose between GitHub Actions, n8n workflow, or shell script for full CI/CD coverage.
