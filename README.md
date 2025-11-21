# Zed Rules

A comprehensive configuration system for AI-powered development with Zed editor, providing structured rules, commands, and workflows for intelligent code assistance.

## Table of Contents

- [Overview](#overview)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Rules](#rules)
- [Commands](#commands)
- [Workflows](#workflows)
- [Resources](#resources)

## Overview

Zed Rules is a curated collection of AI assistant configuration files that enhance development workflows through:

- **Comment-free code philosophy** - Clear naming and structure over inline documentation
- **Memory bank system** - Context preservation across AI sessions
- **Structured workflows** - From exploration to production-ready PRs
- **Quality gates** - Automated checks for commits, PRs, and code review

All rules are automatically combined into `AGENTS.md` via the `prepare` script.

## Quick Start

**Option 1: Copy to Your Project**

Copy the `zed-rules` directory structure to your project:

```
your-project/
├── rules/      # AI behavior rules (.md files)
├── commands/   # Custom workflows (.md files)
└── templates/  # Plan and command templates
```

**Option 2: Add to Workspace (Recommended)**

Add this repository as a workspace folder in Zed to use across multiple projects.

**Build AGENTS.md:**

```bash
npm run prepare
```

This concatenates all rules from `rules/*.md` into a single `AGENTS.md` file.

## Project Structure

```
zed-rules/
├── rules/          # Core AI behavior rules
│   ├── coding.md   # Clean code principles
│   ├── core.md     # Communication and behavior
│   ├── memory.md   # Memory bank system
│   └── tools.md    # MCP tools configuration
├── commands/       # Workflow commands
├── templates/      # Reusable templates
├── AGENTS.md       # Combined rules (auto-generated)
└── package.json    # Build scripts
```

## Rules

Rules define AI behavior and are combined into `AGENTS.md`. Located in `rules/`:

### `coding.md`
Clean code principles and naming conventions:
- Comment-free code philosophy
- Intention-revealing names
- Small, focused, testable functions
- Simple control flow (early returns)

### `core.md`
Communication style and general behavior:
- Natural, conversational tone
- No unnecessary apologies
- Fact validation with sources
- Direct, concise responses

### `memory.md`
Memory bank system for context management:
- Structured documentation hierarchy
- Session-independent context
- Plan and Act mode workflows
- Update rules and triggers

### `tools.md`
MCP (Model Context Protocol) tools configuration:
- Tool priority hierarchy
- Usage guidelines per tool
- Error handling patterns
- Documentation sync procedures

## Commands

Custom workflows invoked with `/command-name`. Located in `commands/`:

### Planning

- **`alternatives.md`** - Generate 2-3 viable approaches with pros/cons and recommendation
- **`plan-rules.md`** - Detailed planning rules for actionable plans (use in Plan Mode)
- **`plan-from-conv.md`** - Generate plan prompts from conversation context
- **`masterplan-new.md`** - Create comprehensive masterplans for complex, multi-stage features
- **`masterplan-update-status.md`** - Update plan status, PR links, and progress markers

### Exploration

- **`explore.md`** - Explore new ideas from raw concepts to partially-defined features
- **`quickwins.md`** - Suggest up to 3 quick-win improvements (≤1h each) across workspace
- **`deep-think.md`** - Structured problem-solving with sequential reasoning

### Analysis

- **`investigate.md`** - Deep code analysis and investigation

### Code Review

- **`review.md`** - Systematic code review
- **`commit.md`** - Create conventional commits with auto-generated titles
- **`pr-new.md`** - Prepare new pull requests
- **`pr-update.md`** - Update existing PR descriptions and status
- **`conflicts.md`** - Resolve merge conflicts with context-aware approach

### Documentation

- **`docs.md`** - Write and review technical documentation (APIs, architecture, guides)

### Memory Management

- **`memory-init.md`** - Initialize memory bank structure
- **`memory-update.md`** - Update project context and documentation

## Workflows

### Simple Feature/Issue (Single PR)

For focused features requiring structured planning:

**1. Explore Options**

```bash
# Get alternatives
/alternatives "Add rate limiting to /api/users endpoint"

# Or use deep-think first for complex issues
/deep-think "Best approach for API rate limiting"
/alternatives "Implement rate limiting based on deep-think analysis"
```

**2. Create Plan (Plan Mode)**

Switch to Zed Plan Mode, then:

```bash
/plan-rules
# Create detailed plan with TODO list, tests, acceptance criteria
```

**3. Execute Plan**

Stay in Plan Mode and execute step-by-step.

**Use for:** Single features, bug fixes, refactoring, optimizations, API changes

---

### Complex Feature (Multi-Stage/Multi-PR)

For features spanning multiple PRs or repositories:

**1. Deep Thinking (Recommended)**

```bash
/deep-think "Implement real-time notifications with EventBridge"
```

**2. Create Masterplan**

```bash
/masterplan-new "Real-time notifications feature"
# Outputs: plans/[username]/[feature-name].md
```

**3. Plan Each PR (Plan Mode)**

For each PR in masterplan:

```bash
/plan-rules
# Create detailed plan for specific PR
```

**4. Execute & Update**

Implement in Plan Mode, then:

```bash
/masterplan-update-status plans/username/feature.md
```

**Use for:** Multi-repo features, 3+ sequential PRs, phased rollouts, architectural changes

---

### Quick Improvements

```bash
# Get up to 3 quick wins (≤1h each) across workspace
/quickwins

# Scope to specific area
/quickwins "focus on API layer"
```

---

### Exploration

```bash
# Explore new ideas or features
/explore "Real-time collaboration feature"
```

## Resources

- [Zed Editor](https://zed.dev/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Clean Code Principles](https://github.com/ryanmcdermott/clean-code-javascript)

---

**Note:** This project follows a comment-free code philosophy. All design decisions and architecture are documented in Markdown files, not in code comments.