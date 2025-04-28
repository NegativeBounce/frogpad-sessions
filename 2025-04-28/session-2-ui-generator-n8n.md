
# 🧠 Session Report: GPT-Based UI Generator — Session 2

**Date:** 2025-04-20  
**Session:** 2 of 3  
**Objective:** Begin building the n8n workflow to automate the GPT-based UI Generator

---

## 🎯 Goal

Create a structured n8n automation that:
- Accepts user input via n8n form
- Sends a system message + prompt to GPT
- Parses the GPT response into structured JSON
- Outputs ready-to-use code + CLI install commands

---

## 🧩 Inputs Used

### 🔷 Form Fields Submitted
- What kind of research will this UI be for
- Will it have selections that a user can select
- Will the user be required to fill in a text box for their query
- Do you want citations provided in a card?
- Do you want a card that provides text with an answer to a query?

### 🔷 Prompt to GPT
```txt
Build a form with the following:
- {{ $json['What kind of research will this UI be for'] }}
- {{ $json['Will it have selections that a user can select'] }}
- {{ $json['Will the user be required to fill in a text box for their query'] }}
- {{ $json['do you want citations provided in a card'] }}
- {{ $json['do you want a card that provides text with an answer to a query?'] }}
- A submit button at the bottom
- Validation for required field
```

---

## 🧠 GPT Output Structure

### ✅ Output Formatting Goal
We defined a JSON format to use in the Structured Output node:

```json
{
  "components_to_install": [
    "npx shadcn@latest add input",
    "npx shadcn@latest add checkbox",
    "npx shadcn@latest add button",
    "npx shadcn@latest add form"
  ],
  "files_to_create_or_update": [
    {
      "path": "src/App.tsx",
      "language": "tsx",
      "content": "/* Full JSX output from GPT */"
    }
  ],
  "functional_summary": "Describes layout and logic of the form.",
  "build_notes": [
    "Ensure react-hook-form is installed.",
    "Wire submit to backend or webhook as needed."
  ]
}
```

---

## ✅ Completed

- Built and tested GPT Agent in n8n with form input
- Extracted valid React code for App.tsx from GPT
- Converted GPT output into structured JSON format
- Defined schema for use in follow-up actions (rendering, Git commit, preview UI)

---

## 🧠 Memory Reset Recovery Note

When you return, you can begin:
- **Session 3: Create example output from a real UI instruction**
- OR extend this workflow by writing files to disk or Git

---
