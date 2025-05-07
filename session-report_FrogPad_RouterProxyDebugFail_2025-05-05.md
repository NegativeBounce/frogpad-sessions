# Session Report: FrogPad Router Proxy Debug Failure  
**Date:** 2025-05-05  
**Project:** FrogPad.AI  
**Focus:** Debugging OpenAI Proxy Failure on `router.frogpad.ai`  
**Result:** ❌ No resolution — persistent 405 and invalid API key errors  

---

## ✅ Session Objectives
- Validate OpenAI proxy configuration
- Test proxy connectivity to n8n, curl, and external POST requests
- Review Nginx + Node.js integration
- Trace `OPENAI_API_KEY` injection pathway
- Validate .env loading logic, ports, bindings, UFW, systemd state

---

## 🔄 Key Actions Taken

### 1. Verified Directory Structure & Routing
- Navigated to `~/router-backend/` and `~/routes/openai-proxy.js`
- Confirmed correct Express route export and mounting to `/openai-proxy`
- Verified router is listening on port `8081` and Node.js service is live

### 2. API Curl Failures
- All curl POSTs to `https://router.frogpad.ai/openai-proxy` returned:
  ```
  405 Not Allowed
  ```
- Direct `localhost:8081/openai-proxy` worked but failed due to:
  ```
  Incorrect API key provided: undefined
  ```

### 3. Environment & API Key Diagnostics
- Verified `.env` file exists at `/root/router-backend/.env`
- Confirmed presence of `OPENAI_API_KEY=sk-...` in .env
- Multiple attempts to load via:
  ```js
  import { config } from 'dotenv';
  config();
  ```
  still led to `undefined` at runtime.

### 4. Nginx Reverse Proxy
- Verified `nginx.conf` and `/etc/nginx/sites-available/default` have:
  ```nginx
  location /openai-proxy {
      proxy_pass http://localhost:8081/openai-proxy;
      ...
  }
  ```
- Reloaded Nginx → Conflict due to Node.js already using port 443
- Nginx failed with bind error: `bind() to 0.0.0.0:443 failed (98)`

### 5. Node.js Secure Binding (Port Conflict)
- Switched Node to `https.createServer(...)` on 443 — led to port conflicts
- Returned to plain port 8081 to isolate application logic from cert handling

---

## 🚨 Key Issue Identified
- `process.env.OPENAI_API_KEY` resolves to `undefined` inside `openai-proxy.js`
  despite `.env` being properly located
- Potential causes (not confirmed):
  - Environment not loaded at runtime
  - Node server not restarted after env change
  - .env path mismatch in production context
  - Possible overwrite from another global setting

---

## 🧠 Memory Reset Recovery Note
> Resume with: Verifying environment load using a direct `console.log(process.env)` line in the server boot block and potentially using `dotenv-expand`. Also consider switching to a controlled script (`start.js`) that loads env variables explicitly before any module imports.

---

