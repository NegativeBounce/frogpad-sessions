# 🧩 Frogpad.AI Ecosystem – Full Session Agenda & Expansion Roadmap

**Last Updated**: 2025-04-21  
**Context**: Live frontend UI connected to `n8n` AI Agent workflow via secure webhook. Core pipeline working end-to-end from query to AI response.

---

## 🔐 Session 0: Add Login Page / UI Gate
**Purpose**: Prevent public abuse of the AI-powered frontend.
- Add a secure, minimal login or gate mechanism
- Options:
  - Basic Auth (temporary)
  - JWT-based login with Supabase
  - Invite-only or tokenized access for early users
- Prevent anonymous POSTs that burn OpenAI credits

---

## ✅ Completed Sessions

### **Session 1: Tie Front-End UI Query to n8n**
- UI form submission posts to `https://n8n.frogpad.ai/webhook/ui-agent`
- Webhook receives query and responds with JSON `{ "status": "received" }`

### **Session 2: Answer the Query from the UI and Display It**
- n8n AI Agent processes query
- Returns structured response:
  ```json
  {
    "answer": "...",
    "sources": [ ... ]
  }
  ```
- Displayed in the frontend using cards

### **Session 3: Display Citations and Resources**
- Frontend styles and formats citations
- Uses `source[].title`, `url`, `type`, etc.
- Cards, hyperlinks, metadata presentation

---

## 🔜 Upcoming Sessions

### **Session 4: Save Full Query Report**
- Combine query + answer + sources into a report
- Output as structured JSON or formatted string
- Return to frontend or prepare for archive (GitHub or DB)

### **Session 5: Route All Info to a Database**
- Connect n8n to Postgres or Supabase
- Insert records for query sessions:
  - `query`, `answer`, `sources[]`, `timestamp`, etc.
- Enable future filtering, querying, analytics

---

## 🧪 Optional + Creative Session Ideas

### **Session 6: Add Dropdowns and Filters**
- Add topic/category selectors to form (`legal`, `finance`, `tech`, etc.)
- Pass to AI prompt for better context

### **Session 7: Add Loading/Failure Feedback in UI**
- Add spinners, toast notifications, and error boundary for fetch() calls

### **Session 8: Add Agent Selector (Prompt Control)**
- UI dropdown to choose “Research Style” (e.g. “Simple”, “Detailed”, “Summary”)
- Controls prompt style or model params in n8n

### **Session 9: PDF Report Export**
- Convert the structured report into a downloadable PDF
- Trigger from frontend or backend

### **Session 10: GitHub Save Integration**
- Save reports or structured summaries to a private GitHub repo
- Use GitHub API from n8n

### **Session 11: User Session Logging & Analytics**
- Log basic metadata: IP, location, query type, device type
- Visual dashboard via Supabase or Outerbase

### **Session 12: Response Versioning and Replay**
- Allow user to “regenerate” or replay past queries
- Store past answers, compare across agents

### **Session 13: API Usage Cost Tracking**
- Track number of calls, estimate token cost
- Summarize daily burn and alert if needed

### **Session 14: Integrate Voice Input**
- Add microphone input to frontend
- Transcribe with Whisper or another tool before submission

### **Session 15: Team Collaboration Mode**
- Allow teams to log into a workspace
- Share queries, tag research threads, comment on reports

---

## 🧠 Memory Reset Recovery Note
> The system is now live and stable from query to structured answer. Creative and security-focused expansion is the next stage. Login gating is prioritized to protect OpenAI credits.
