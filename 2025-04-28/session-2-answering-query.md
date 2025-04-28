# 🧠 Session 2 Report – Answering the Query from the UI and Displaying It

**Date**: 2025-04-21  
**Objective**: Update the `n8n` workflow to process queries from the frontend UI, use the AI Agent to generate a structured answer, and return that answer to the UI for display.

---

## ✅ Summary of Steps

1. **n8n Workflow Enhanced**
   - Webhook: `POST https://n8n.frogpad.ai/webhook/ui-agent`
   - Trigger receives: `{ "query": "user submitted value" }`
   - Connected Nodes:
     - AI Tools Agent Node (structured output prompt)
     - Structured Output Node
     - Respond to Webhook

2. **Prompt Design**
   - Provided the AI Agent with a formatted prompt:
     ```json
     {
       "answer": "string",
       "sources": [
         {
           "id": "1",
           "title": "string",
           "url": "string",
           "type": "string"
         }
       ]
     }
     ```

3. **Test Performed Using Webhook-Test**
   - Test Endpoint: `https://n8n.frogpad.ai/webhook-test/ui-agent`
   - Test Query:
     ```bash
     curl -X POST https://n8n.frogpad.ai/webhook-test/ui-agent \
       -H "Content-Type: application/json" \
       -d '{ "query": "What are the main privacy regulations in Germany under GDPR?" }'
     ```
   - Response Returned:
     ```json
     {
       "answer": "Germany enforces GDPR through ...",
       "sources": [
         {
           "id": "1",
           "title": "Official GDPR Guide",
           "url": "https://gdpr-info.eu",
           "type": "Regulation"
         }
       ]
     }
     ```

4. **Frontend Already Compatible**
   - No frontend code changes required during this session.
   - Frontend now receives structured JSON and displays the `answer` and `sources` from the n8n AI workflow.

---

## 🔗 Endpoints Used
- `https://gateway.frogpad.ai` – Live UI
- `https://n8n.frogpad.ai/webhook/ui-agent` – Production webhook
- `https://n8n.frogpad.ai/webhook-test/ui-agent` – Test webhook

---

## 📌 Next Steps (Session 3)
- Enhance frontend UI to style and format citations and sources returned from the `sources[]` array
- Improve readability, clickable URLs, and metadata display (e.g., source type)

---

## 🧠 Memory Reset Recovery Note
> The `n8n` AI Agent now successfully receives a query, processes it, and returns a structured answer with sources to the frontend. The UI receives and logs/display the structured result. Next step is to format and style the citations on screen.
