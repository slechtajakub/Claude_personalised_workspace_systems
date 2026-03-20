# Personalised workspace systems

Personal AI-powered workspace setup combining Claude Projects and Cowork OS 
for education administration, rugby club administration and workflow automation. Two complementary systems 
demonstrating practical system design, context management, and AI integration.

## 🎯 Overview

This repository documents two personalized AI workspace systems built for different 
contexts — one cloud-based (claude.ai Projects), one local filesystem-based (Claude Cowork).

**Why this matters:** Shows how to architect persistent context, role-switching, 
and memory management in AI-driven workflows — skills directly applicable.

---

## 📁 System 1: Claude Projects — "Jakub / Workspace"

**Type:** Cloud-based, role-switching system  
**Platform:** claude.ai Projects  
**Primary Use:** Multi-context AI mentoring (Education, Business (Rugby Club), IT, Career)

### Architecture

```
Personal Context (identity + skills + goals)
        ↓
Custom Instructions (role definitions + communication rules)
        ↓
Memory (persistent learning notes between sessions)
```

### Key Features

- **5 Dynamic Roles**: EdTech Specialist, Life Coach, IT Mentor, Career Recruiter, Operations Manager
- **Persistent Memory**: Learns about projects, blockers, solutions across sessions
- **Context-Aware Responses**: Changes behavior based on query type (IT question → Senior Mentor mode)

### How Role-Switching Works

```
Input: "Jak vyřeším tento problém s Pythonem?"
→ Activates: role_it (Senior Mentor mode)
→ Output: Assumes Python basics known, focuses on patterns + best practices

Input: "Rugby Plus administrativní problém"
→ Activates: role_business (Operations Manager mode)
→ Output: Efficiency + automation thinking, not generic advice

Input: "Potřebuju pomoct s CV"
→ Activates: role_career (IT Recruiter mode)
→ Output: Feedback on transferable skills, portfolio gaps, missing certifications
```

### What You Learn Here

- **Prompt Engineering**: Custom instructions as behavior controller
- **System Design**: Role-based context switching (analogous to RBAC in software)
- **Memory Management**: Persistent context between sessions (like session state in apps)

### Custom Instructions Structure

```xml
<personal_context>
  <identity>           <!-- Who I am -->
  <professional_background>  <!-- What I do -->
  <technical_skills>   <!-- Current level of each skill -->
  <certifications>     <!-- Credentials -->
  <projects>          <!-- Portfolio evidence -->
  <goals>             <!-- Short/long term targets -->
  <communication>     <!-- How to respond to me -->
  <context_rules>     <!-- Role definitions -->
    <role_it>
    <role_career>
    <role_business>
    <role_education>
    <role_lifestyle>
```

---

## 📂 System 2: Cowork OS — Filesystem-Based Workspace

**Type:** Local, file-system driven  
**Platform:** Claude Cowork (desktop app)  
**Primary Use:** Project-specific workflows with live data connectors

### Architecture

```
Cowork OS/
├── Claude.md           (orchestrator instructions)
├── Memory.md           (workspace-level knowledge)
├── Škola/              (Education project)
│   ├── Claude.md       (EdTech role + school context)
│   ├── Memory.md       (classes, student notes, results)
│   └── [project files]
├── Rugby Plus/         (Sports club project)
│   ├── Claude.md       (Operations role)
│   ├── Memory.md       (team, budget, schedule, marketing)
│   └── [project files]
└── [future projects]
```

### Key Features

- **Hierarchical Context**: Each folder = independent Claude personality
- **File-Based Memory**: `.md` files as knowledge base (fully git-version-controllable)
- **Live Connectors**: Gmail, Google Calendar, Google Sheets, Google Drive (real-time data)
- **Skills System**: Reusable workflows with slash commands (`/memory-create`, `/evaluate_tests`, etc.)
- **Offline-First**: All data local, no cloud dependency
- **Plugin Support**: Cowork OS plugin handles `/memory-create`, `/memory-delete`, `/subfolders`, `/begin`

### Example Workflow: Test Evaluation Pipeline

```bash
# Trigger workflow in Cowork, Škola/ folder
Input:  /evaluate_tests testy_7A.pdf

Claude then:
  1. Reads Škola/Claude.md       → understands EdTech Assistant role
  2. Reads Škola/Memory.md       → knows student names, learning gaps, class dynamics
  3. Fetches via Google Sheets   → gets live student roster from connector
  4. Executes /evaluate_tests skill:
     - Extracts student names + scores from PDF (OCR)
     - Fuzzy-matches to roster (handles name variations)
     - Imports results to Google Sheets automatically
     - Updates Memory.md with analysis
  5. Returns report:
     - Score distribution
     - Outliers (students who need follow-up)
     - Personalized notes 

Next evaluation:
  /evaluate_tests testy_7A_březen.pdf
  → Claude already knows context, no re-explanation needed
```

**Real Impact:** 2 hours of manual grading + entry → 5 minutes automated

### What You Learn Here

- **System Architecture**: Filesystem as database, version control as audit trail
- **Context Propagation**: Maintaining state across hierarchical folder structures
- **Connector Integration**: Live API integration without building full backend
- **Skill Design**: Building reusable, documented processes (like test fixtures)
- **Automation**: Reducing repetitive manual work through workflow optimization
- **Data Pipelines**: OCR → fuzzy matching → database → reporting


# EdTech Assistant — ZŠ Labyrinth

## My Role
I help Jakub prepare materials for:
- Geography (zeměpis)
- Biology (přírodopis)  
- Physical Education (TV)

Primarily working with 6th-9th grade students (age 11-15).

## Key Responsibilities
- Create age-appropriate tests and worksheets
- Evaluate student performance (import from PDFs)
- Suggest teaching approaches
- Adapt material for students with different learning paces
- Track class progress and individual struggles

## Communication Style
- Direct feedback on material clarity
- Suggest practical activities (not just theory)
- Propose differentiation strategies for mixed-ability classes
- Focus on what actually works in classroom (not generic pedagogy)

## Important Constraint
- Use simple language, avoid jargon
- Consider 12-year-old understanding level
- Test/material length: realistic for 45-min lessons
```

---

## 📚 Resources & References

- **Original Cowork OS Concept:** Paul J Lipsky (https://www.youtube.com/watch?v=cJ2QCyr3yzU&t=32s&pp=ygUJY293b3JrIG9z0gcJCcMKAYcqIYzv)
- **Claude Documentation:** 
- **My Learning Journey:** (https://slechtajakub.cz)

---

## About

**Built by:** Jakub Šlechta  
**Background:** Teacher → IT Enthusiast
**Current Roles:** 
- Teacher (Geography, Biology, PE) at ZŠ Labyrinth
- Founder & Operations Manager, Rugby Plus (80 kids, 10 coaches)

**Certifications:**
- Python Academy (Engeto)
- Junior Tester (Codebiters)
- AI Fundamentals (IBM)
- SQL Fundamentals (Simplilearn)

**Contact:**
- GitHub: [@slechtajakub](https://github.com/slechtajakub)
- LinkedIn: [slechtajakub](https://www.linkedin.com/in/slechtajakub)
- Portfolio: [slechtajakub.cz](https://slechtajakub.cz)
