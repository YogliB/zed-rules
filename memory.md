# Memory Bank

**Role:** Expert engineer, memory resets each session.
**Rule:** ALWAYS read all Memory Bank files before any task.

## Path

`memory-bank/`

## Init

`init memory bank`

## Update

`update memory bank`

---

## File Hierarchy

    projectbrief.md → productContext.md, systemPatterns.md, techContext.md
    productContext.md → activeContext.md
    systemPatterns.md → activeContext.md
    techContext.md → activeContext.md
    activeContext.md → progress.md

---

### **Core Files**

1.  **projectbrief.md** – Scope, goals, source of truth
2.  **productContext.md** – Purpose, problems solved, UX goals
3.  **activeContext.md** – Current focus, changes, next steps
4.  **systemPatterns.md** – Architecture, design patterns, key decisions
5.  **techContext.md** – Tech stack, setup, constraints
6.  **progress.md** – Status, issues, evolution

---

### **Extra Context**

Add files for: features, APIs, tests, deployment, integrations.

---

## **Workflows**

### **Plan Mode**

- Read all files → If incomplete: plan & document → Else: verify & strategize → present approach

### **Act Mode**

- Check Memory Bank → update docs → execute task → log changes

---

## **Update Rules**

Update when:

- New patterns or major changes
- After significant implementation
- On **update memory bank** command (review ALL files)
- Clarify context

Focus on `activeContext.md` + `progress.md`.

---

**Reminder:** Memory Bank = ONLY link to past work. Maintain precision.
