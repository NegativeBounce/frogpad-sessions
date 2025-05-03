# Session Report: Prompt Engine Submission Flow ✅
**Date:** 2025-05-03  
**Component:** FrogPad Prompt Engine  
**Scope:** Wire up schema-based form → backend API → PostgreSQL storage

---

## ✅ Steps Completed

1. **Frontend** (`prompt-engine-ui-client`):
   - Disabled manual `id` entry
   - Rendered JSON schema as form
   - Skipped fields: `id`, `variables`, `metadata`
   - Rebuilt production UI → `/var/www/html`

2. **Backend** (`prompt-engine-api`):
   - Updated `createPrompt()` to exclude manual `id`
   - Handled PostgreSQL insert via `name`, `description`, `template`, `variables`, `metadata`
   - Used `JSON.stringify(variables)` for safe `jsonb` inserts
   - Restarted API using `pm2`

3. **Database (PostgreSQL)**:
   - Renamed `title → name`
   - Added `description TEXT`
   - Confirmed table schema: `id UUID`, `variables JSONB`, `metadata JSONB`

4. ✅ **Successfully submitted a prompt from UI to DB**

---

## 🧠 Next Steps

1. Add prompt listing page
2. Start wiring into GPT proxy workflows
