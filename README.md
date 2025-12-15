# Keboola Xmas Engineering Challenge

> "A lot of things exist today, but they're scattered, unfinished, naturally aging over time. Package it with a bow."

---

## Goal

Build a **self-healing knowledge system** for Claude Code + Keboola:

```
Claude masters everything in Keboola
         ↓
    Hits a problem?
         ↓
    Auto-report GitHub Issue
         ↓
    AI proposes fix → Human review → Merge
         ↓
    Knowledge base updated
         ↓
    Claude knows next time
```

---

## Three Pillars

### 1. Complete Keboola Knowledge

**For end-users:**
- Understands "Keboola lingo" (workspace, branch, bucket, configuration...)
- Knows UI workflows and navigation
- Avoids common pitfalls

**For developers:**
- Can write Python code for any Keboola API
- Knows when to use MCP vs write custom code
- Deploys to Custom Python, integrates into Flows
- Can develop components (existing ai-kit)

**Boilerplates:**
- Data app (Streamlit + Keboola)
- Custom Python component
- Ex/Wr component
- Python/JS app with Keboola backend

### 2. Error Reporting

When Claude encounters:
- API errors
- Outdated documentation
- Missing pitfall
- Non-working procedure

→ Automatically creates GitHub Issue with structured report

### 3. Validation & Auto-Update Loop

```
GitHub Issue (auto-reported)
         ↓
    AI Triage (valid? category? confidence?)
         ↓
    [high confidence] → AI proposes PR
         ↓
    Human review → Merge
         ↓
    Knowledge base updated
```

---

## Structure

```
keboola/claude-knowledge/
│
├── plugins/
│   ├── keboola-core/          # NEW: API skills, lingo, pitfalls
│   ├── keboola-deploy/        # NEW: Custom Python, Flow integration
│   ├── component-developer/   # EXISTING: Polish
│   ├── dataapp-developer/     # EXISTING: Polish
│   └── developer/             # EXISTING: Keep
│
├── boilerplates/              # NEW: Cookiecutter templates
│
└── validation/                # NEW: Hooks + GH Actions
    ├── hooks/                 # Error reporter
    └── workflows/             # Triage, propose-fix, auto-update
```

---

## Success Criteria

- [ ] Claude writes working Python code for any Keboola API endpoint
- [ ] Zero "workspace ID confusion" issues
- [ ] End-user describes what they want in business language, Claude does it
- [ ] 80%+ issues correctly auto-triaged
- [ ] Knowledge base continuously improves

When I ask Claude Code for anything Keboola-related, I shouldn't have to scout documentation or watch over Claude. I need Claude Code to be smarter than me. When developing with E2B, I had to download all their documentation and create a skill (using https://github.com/anthropics/skills/tree/main/skills/skill-creator) - then Claude Code suddenly became an E2B expert. I want the same effect for Keboola. A lot of work already exists in https://github.com/keboola/ai-kit

Improve it, add examples, package it with a bow, and deliver to end-users.

---

## Open Questions

1. MCP extension vs skills for writing code?
2. Boilerplates in this repo or standalone?
3. Error reporting opt-in or default?
4. Threshold for auto-merge vs human review?
