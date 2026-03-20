# System Design: Claude Projects vs. Cowork OS

Architectural comparison and decision framework for when to use each system.

---

## Quick Comparison

| Aspect | Claude Projects | Cowork OS |
|---|---|---|
| **Location** | Cloud (claude.ai) | Local (your computer) |
| **Storage Format** | Proprietary Anthropic | Markdown files (.md) |
| **Accessibility** | Web only | Desktop + mobile (via folder sync) |
| **Setup Time** | 5 minutes | 30 minutes |
| **Offline Access** | No | Yes |
| **Structure** | Flat (one project) | Hierarchical (folders within folders) |
| **Role Switching** | Via context rules | Via folder navigation |
| **Memory Format** | Hidden (sidebar UI) | Visible (.md files) |
| **Connector Support** | Limited (Cowork-specific) | Via MCP servers |
| **Scalability** | Create multiple projects | Infinitely many subfolders |

---

## Architectural Differences

### Claude Projects Architecture

```
┌─────────────────────────────────────┐
│        Claude.ai (Cloud)            │
├─────────────────────────────────────┤
│                                     │
│   ┌─────────────────────────────┐   │
│   │  Claude Project             │   │
│   │  "Jakub / Workspace"        │   │
│   │                             │   │
│   │  ┌──────────────────────┐   │   │
│   │  │ Custom Instructions  │   │   │
│   │  │ (5 roles defined)    │   │   │
│   │  └──────────────────────┘   │   │
│   │           ↓                 │   │
│   │  ┌──────────────────────┐   │   │
│   │  │ Memory               │   │   │
│   │  │ (learned facts)      │   │   │
│   │  └──────────────────────┘   │   │
│   │           ↓                 │   │
│   │  ┌──────────────────────┐   │   │
│   │  │ File Uploads         │   │   │
│   │  │ (shared documents)   │   │   │
│   │  └──────────────────────┘   │   │
│   │                             │   │
│   └─────────────────────────────┘   │
│                                     │
└─────────────────────────────────────┘

Pattern: Everything in one project, 
         roles are behavioral rules
```

### Cowork OS Architecture

```
┌─────────────────────────────────────────────┐
│  Your Computer (Local Filesystem)           │
├─────────────────────────────────────────────┤
│                                             │
│  Cowork OS/                                 │
│  ├── Claude.md (orchestrator)               │
│  ├── Memory.md (workspace facts)            │
│  │                                         │
│  ├── Škola/ (Project 1)                     │
│  │   ├── Claude.md (EdTech role)            │
│  │   ├── Memory.md (class data)             │
│  │   └── [files]                            │
│  │                                         │
│  ├── Rugby Plus/ (Project 2)                │
│  │   ├── Claude.md (Operations role)        │
│  │   ├── Memory.md (team data)              │
│  │   └── [files]                            │
│  │                                         │
│  └── IT/ (Project 3)                │
│      ├── Claude.md (Engineer role)          │
│      ├── Memory.md (scripts/configs,code)        │
│      └── [files]                            │
│                                             │
│  [Git version control covers everything]   │
│                                             │
└─────────────────────────────────────────────┘

Pattern: Hierarchy of folders, each folder
         is a self-contained project
```

---

## Data Flow Comparison

### Claude Projects: Query Execution

```
You ask question in chat
         ↓
Claude reads custom instructions (all 5 roles + your context)
         ↓
Claude detects query type (IT? Career? Business? etc.)
         ↓
Claude activates appropriate role
         ↓
Claude checks memory ("what do I know about this?")
         ↓
Claude returns role-specific answer

Loop: Same project, different roles
```

### Cowork OS: Query Execution

```
You navigate to specific folder (e.g., Škola/)
         ↓
Claude reads:
  - Cowork OS/Claude.md (orchestrator)
  - Cowork OS/Memory.md (workspace facts)
  - Škola/Claude.md (EdTech role)
  - Škola/Memory.md (class facts)
         ↓
You ask question in that folder's context
         ↓
Claude responds with all context loaded
         ↓
If you navigate to Rugby Plus/
Claude immediately reloads all Rugby Plus context

Loop: Same system, different folder = different project
```

---

## Decision Framework

### Use Claude Projects When:

✅ **Single discipline with multiple roles**
```
Example: "I'm a consultant working in QA, but also coach, mentor, dad"
→ One project, five roles, switch based on question type
```

✅ **Instant accessibility matters**
```
Example: "I need to work from phone, tablet, laptop without sync setup"
→ Cloud access anywhere immediately
```

✅ **Sharing context with others**
```
Example: "I want to share this project with my team"
→ Cloud-based, easy sharing, no local setup needed
```
---

### Use Cowork OS When:

✅ **Multiple separate projects**
```
Example: "I have Škola, Rugby Plus, Automation — distinct work"
→ Separate folder per project, each with own context
```

✅ **Hierarchical organization**
```
Example: "Automation project has subfolders: Testing, Scripts, Docs"
→ Folders naturally represent structure
```

✅ **Complex workflows with state**
```
Example: "Tests need results stored, analyzed, reported"
→ Memory.md persists across runs, Git tracks history
```
--

## Hybrid Approach (Recommended)

The best strategy: **Use both**

```
Claude Projects
├─ Quick daily feedback (5 min sessions)
├─ Role-switching for advice
├─ Mentoring relationships
└─ Instant mobile access

     ↑↓ (Sync memory occasionally)

Cowork OS
├─ Real work (1-2 hour sessions)
├─ Project-specific workflows
├─ Version-controlled systems
└─ Offline-capable, desktop

Workflow:
Morning: "Quick questions" in Claude Projects chat
Afternoon: Real work in Cowork OS folders
Evening: Review, record key learnings in Memory.md
```

---