# 🧩 MCP Tools Quick Guide

## ✅ Core Principles

- Use **local knowledge first**; MCP only if needed.
- **Briefly state reason** before tool use.
- Pick **most specific MCP** (see priority).
- Don’t repeat tool descriptions.

---

## 🔝 Priority

1. `grep` – code search  
2. `figma` – design/UI  
3. `fetch` – remote data  
4. `playwright` – browser automation  
5. `context7` – contextual analysis  
6. `sequentialthinking` – multi-step reasoning  

---

## 📡 Tool Rules

- **fetch:** HTTP GET/POST; full URL; prefer JSON; summarize large data.  
- **figma:** Inspect layouts, tokens; sync with docs.  
- **grep:** Precise queries; minimal snippets; no auto-commit.  
- **playwright:** UI tests; avoid heavy crawling; summarize results.  
- **context7:** Extract, analyze, and enrich context from text or structured data; prioritize semantic clarity; return concise insights.  
- **sequentialthinking:** Plan → simulate → evaluate workflows.  

---

## 🧠 Docs Sync

- Log MCP outputs to internal docs with **timestamp + tool + summary**.  
  Example:  
  `[MCP: fetch | 2025-11-02 | Retrieved API spec]`  

---

## ⚠️ Errors

- Retry once with simpler params; else summarize or clarify.

---

## ➕ Extensibility

- Add new MCP under guidelines; update priority if needed.

---

## 🔍 Summary Table

| Tool               | Role        | Use                        |
| ------------------ | ----------  | -------------------------- |
| fetch              | Retrieval   | JSON/docs                 |
| figma              | Design      | Layout/tokens             |
| grep               | Code        | Repo queries              |
| playwright         | Automation  | UI tests                  |
| context7           | Analysis    | Context extraction/enrich |
| sequentialthinking | Reasoning   | Workflow planning         |
