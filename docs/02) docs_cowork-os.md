# Cowork OS: Filesystem-Based Workspace

Deep dive into the second workspace system — local, file-driven organization with hierarchical projects and live connectors.

## Overview

**Cowork OS** (on Claude Cowork desktop app) is a filesystem-based workspace where everything is **local files** organized hierarchically.

Instead of:
- Cloud storage
- Proprietary memory format
- Web-only access

You get:
- Local `Claude.md` + `Memory.md` files
- Git version control
- Offline access
- Portable backup

---

## Architecture

### Core Structure

```
Cowork OS/
├── Claude.md                 (Orchestrator role)
├── Memory.md                 (Workspace-level facts)
│
├── Škola/                    (Project: Education)
│   ├── Claude.md             (EdTech Assistant role)
│   ├── Memory.md             (Classes, students, results)
│   ├── [lesson files]
│   ├── [test PDFs]
│   └── [materials]
│
├── Rugby Plus/               (Project: Sports Club)
│   ├── Claude.md             (Operations Manager role)
│   ├── Memory.md             (Teams, budget, schedule, vision, plans)
│   ├── [team rosters]
│   ├── [training plans]
│   └── [event calendars]
│
│
└── [Future projects...]
```

### How It Works

**When you open Cowork and navigate to Škola/:**

```
Claude Cowork app reads:
  1. Cowork OS/Claude.md      → "I'm orchestrator"
  2. Cowork OS/Memory.md      → "Know about all projects"
  3. Szkola/Claude.md         → "I'm EdTech Assistant"
  4. Szk ola/Memory.md        → "Know about classes, students, results"
  
→ Claude now has full context for that project and switches personality
→ Responds specifically as EdTech person for this folder
```
---

## File Format & Examples

### Claude.md (Root Level)

**Purpose:** Define what Cowork OS is and how Claude should behave overall

```markdown
# Cowork OS — Workspace Orchestrator

## What I Am
I manage multiple projects for Jakub:
- Škola (education)
- Rugby Plus (sports club operations)
- Automation (AI workflows)
- [future projects]

## My Role
- Understand which project you're in
- Load that project's context automatically
- Switch personality based on project
- Coordinate between projects when needed

## Communication
- Direct, practical, no filler
- Focus on results, not process
- Suggest efficiency improvements
- Think in systems

## Projects Summary
See Memory.md for current status of each
```

### Memory.md (Root Level)

**Purpose:** Workspace-level facts, project status, cross-project notes

```markdown
# Cowork OS — Memory

## Project Status

### Škola (Education)
- Status: Active, daily use
- Last update: Today
- Tiers: zeměpis 7.A, přírodopis 6.B
- Key blocker: Test grading time (now automated)

### Rugby Plus  
- Status: Planned setup
- Estimated launch: Next week
- Focus: Operational automation
- Initial goal: Team management + training schedule

```

### Claude.md (Project Level: Škola)

**Purpose:** Define role for this specific project

```markdown
# Škola — EdTech Assistant

## Who I Serve
Jakub Šlechta, teacher at ZŠ Labyrinth
- Subjects: Geography, Biology, Physical Education
- Grades: 6.A, 9.B
- Age range: 11-15 years old

## My Role
Create and optimize educational materials and processes for:
- Test creation (age-appropriate difficulty)
- Worksheet design (variety of formats)
- Student evaluation (track progress)
- Material differentiation (adapt for different levels)
- Time optimization (minimize prep work)

## Key Constraints
- Material must be usable in 45-minute lessons
- Language: Simple, clear, avoid jargon
- Format: Mix of written, visual, interactive
- Differentiation: Some students need simplified versions
- Documentation: Track what works for next year

## Teaching Philosophy I Support
- Active learning (not just reading)
- Practical examples (connect to real world)
- Multiple formats (not everyone learns same way)
- Quick wins (show progress early)
- Building confidence (celebrate small successes)

## What NOT to Do
- Generic pedagogy (I know actual students)
- Over-complicated materials (wastes prep time)
- One-size-fits-all (students have different needs)
- Busywork (everything must have learning purpose)

## Tools I Have Access To
- Google Drive (documents, spreadsheets)
- Google Sheets (tracking, analysis)
- PDF tools (test creation, modification)
- Video integration (can suggest resources)

## Success Metrics
- Student engagement goes up
- Test grades improve
- Prep time goes down
- Materials are reusable next year
```


## Why This Format Works Better

### vs. Claude personalised projects

**Cowork OS advantage:**
- ✅ Files are local (offline access, fast)
- ✅ Version control (git history of all changes)
- ✅ Portable (copy folder = backup)
- ✅ Transparent (read .md files directly)
- ✅ Hierarchical (project within project)

---
