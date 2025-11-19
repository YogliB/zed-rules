# 🧩 MCP Tools Quick Guide

## ✅ Core Principles

- Use **local knowledge first**; MCP only if needed.
- **Briefly state reason** before tool use.
- Pick **most specific MCP** (see priority).
- Don’t repeat tool descriptions.

---

## 🔝 Priority

1. `gh_grep` – code search
2. `figma` – design/UI
3. `fetch` – remote data
4. `playwright` – browser automation
5. `serena` – semantic code editing
6. `sequentialthinking` – multi-step reasoning

---

## 📡 Tool Rules

- **fetch:** HTTP GET/POST; full URL; prefer JSON; summarize large data.
- **figma:** Inspect layouts, tokens; sync with docs.
- **gh_grep:** Precise queries; minimal snippets; no auto-commit.
- **playwright:** UI tests; avoid heavy crawling; summarize results.
- **serena:** Use for semantic code retrieval/editing; symbol-level operations; ideal for large codebases.
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

| Tool               | Role       | Use                     |
| ------------------ | ---------- | ----------------------- |
| fetch              | Retrieval  | JSON/docs              |
| figma              | Design     | Layout/tokens          |
| gh_grep            | Code       | Repo queries           |
| playwright         | Automation | UI tests               |
| serena             | Code Agent | Semantic code editing  |
| sequentialthinking | Reasoning  | Workflow planning      |
