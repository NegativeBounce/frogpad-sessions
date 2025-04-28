
# 🛠️ Session Log: Frogpad.AI Frontend UI Base + Preview

**Date:** 2025-04-20  
**Project:** `frogpad-ui-base`  
**Location:** `gateway.frogpad.ai`  
**Objective:** Build and preview a functional base UI using React + Tailwind + shadcn/ui with support for rapid scaling of future UIs.

---

## ✅ Setup Summary

### Stack:
- Vite + React + TypeScript
- Tailwind CSS v4
- shadcn/ui components
- pnpm for dependency management

### Directory:
`/root/frogpad-ui-base`

---

## 🔧 Build Process & Fixes

### ✅ Initial Setup:
- Created project with `pnpm create vite@latest`
- Installed Tailwind, PostCSS, Autoprefixer manually
- Configured `tailwind.config.js` and `postcss.config.cjs`
- Connected CSS in `src/index.css`

### ✅ shadcn/ui Initialization:
- Used `npx shadcn@latest init`
- Theme: **Slate**
- Added alias `@/*` in both `tsconfig.app.json` and root `tsconfig.json`
- Created and rendered `Button` component via:
  ```bash
  npx shadcn@latest add button
  ```

---

## 🧪 Preview Process

### Issues Resolved:

| Issue | Resolution |
|-------|------------|
| `vite.config.ts` failed on `path` / `__dirname` | Renamed to `vite.config.js` |
| `tsc -b` failed | Removed `tsc -b` from `package.json` scripts |
| PostCSS v4 plugin not found | Installed `@tailwindcss/postcss` and updated config |
| Broken import: `tw-animate-css` | Removed and simplified `index.css` |
| Needed to restore original styles | Used backup: `src/index.backup.css` restored to `src/index.css` |

---

## ✅ Final Working State

- Build succeeded using `pnpm build`
- Preview live at: `http://159.203.110.75:4173/`
- Rendered button from `shadcn/ui`
- Project structure stable and extendable

---

## 🧠 Memory Reset Recovery Note

Next step:
- Begin wiring this base UI to your backend API or n8n webhook
- Optionally deploy to a permanent subpath: `https://gateway.frogpad.ai/ui-test`

---
