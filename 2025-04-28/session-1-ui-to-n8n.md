# 🧠 Session 1 Report – Tie Front-End UI Query to n8n Workflow

**Date**: 2025-04-21  
**Objective**: Connect the live frontend UI at `https://gateway.frogpad.ai` to an `n8n` webhook for processing user-submitted queries.

---

## ✅ Summary of Steps

1. **Created Webhook in n8n**
   - **URL**: `https://n8n.frogpad.ai/webhook/ui-agent`
   - Method: `POST`
   - Response Mode: `Respond to Webhook` (used later in the flow)
   - Temporary response body: `{ "status": "received" }`

2. **Identified Form Component**
   - Located actual form in: `src/pages/Index.tsx`
   - Confirmed submission handler was `handleSubmit`

3. **Modified `handleSubmit` Logic**
   - Removed mock data simulation and replaced with live webhook call:
     ```ts
     const response = await fetch("https://n8n.frogpad.ai/webhook/ui-agent", ...);
     const result = await response.json();
     setResults({
       answer: result?.answer || "",
       sources: Array.isArray(result?.sources) ? result.sources : [],
     });
     ```

4. **Verified Form Submission**
   - Rebuilt app using `npm run build`
   - Ran dev server with `npm run preview`
   - UI now successfully sends queries to n8n and handles safe responses without crashing

---

## 📂 File Modified
- `src/pages/Index.tsx`

## 🔗 Endpoints Touched
- `https://gateway.frogpad.ai` (Frontend)
- `https://n8n.frogpad.ai/webhook/ui-agent` (Backend webhook)

---

## 🔄 Next Steps
- **Session 2**: Process the query and return an actual AI-generated answer
- **Session 3**: Include structured citations and resources in the response
- **Session 4**: Save the entire response payload as a report
- **Session 5**: Route the query+response+metadata into a Postgres or Supabase DB

---

## 🧠 Memory Reset Recovery Note
> The UI now successfully submits queries to `https://n8n.frogpad.ai/webhook/ui-agent`. The next session will enable n8n to return a structured AI-generated answer to render inside the UI.
