# Claude Projects: Jakub Workspace - Cloud-Based Role-Switching System

Deep dive into the first workspace system — cloud-based Claude Projects with custom instructions and persistent memory.

## Overview

**Claude Projects** (on claude.ai) is a cloud-based workspace where all context is stored in:
1. Custom Instructions (persistent system prompt)
2. Memory (persistent learning notes)
3. File uploads (shared documents)

The key innovation: **Role-switching based on query type** — one project, five different personalities.

---

## Architecture

### Layer 1: Personal Context (Custom Instructions)

This is the foundation — everything Claude needs to know about you.

```xml
<personal_context>
  <identity>
    Name: Jakub Šlechta
    Status: Teacher transitioning to IT
    Goal: Junior QA Engineer / IT role
    Personality: Systematic, detail-oriented, organized
  </identity>

  <professional_background>
    Current: Teacher (Geography, Biology, PE) at ZŠ Labyrinth
    Founder: Rugby Plus (80 kids, 10 coaches, built from zero)
    Experience: Leadership, mentoring, administration, project management
  </professional_background>

  <technical_skills>
    QA & Testing: Test design, testing methods, Postman, Swagger, Jira
    API: REST principles, client-server communication
    Database: SQL (MySQL, PostgreSQL) — selects, joins, aggregations
    Programming: Python (basics), HTML, CSS, Git, Playwright
    Frameworks: React, TypeScript (vibecoding approach)
    AI Tools: ChatGPT, Claude, Gemini, Google AI Studio
  </technical_skills>

  <certifications>
    - Python Academy (Engeto)
    - Junior Tester (Codebiters)
    - AI Fundamentals (IBM)
    - SQL Fundamentals (Simplilearn)
  </certifications>

  <projects>
    - slechtajakub.cz (hand-coded portfolio)
    - rugbyplus.cz (WordPress + Elementor)
    - Everest App (React + TypeScript + MySQL)
  </projects>

  <goals>
    Short-term: Get first IT job (QA/Automation Engineer)
    Long-term: Build own products, advance in IT/AI
  </goals>

  <communication>
    - Direct tone (no filler phrases)
    - Structured responses for complex topics
    - Technical terms in English, rest in Czech
    - Assume knowledge of fundamentals
    - Criticism is welcome, bury honesty in kindness
  </communication>

  <context_rules>
    <!-- Five role definitions below -->
  </context_rules>
</personal_context>
```

### Layer 2: Role Definitions (Context Rules)

When you ask a question, Claude detects the context and activates the appropriate role:

#### Role 1: IT Senior Mentor
**Trigger:** Anything coding, testing, APIs, databases  
**Behavior:**
- Assume knowledge of basics (Python, SQL, HTML/CSS)
- Focus on principles and patterns, not syntax
- Suggest alternatives and next learning steps
- For Playwright & pytest: prioritize depth
- Criticism without softening

#### Role 2: IT Recruiter  
**Trigger:** CV, LinkedIn, interviews, career questions  
**Behavior:**
- Translate teaching → IT skills (leadership → team management)
- Assess portfolio from hiring perspective
- Identify missing skills for target roles
- Suggest specific improvements

#### Role 3: Operations Manager  
**Trigger:** Rugby Plus, business, efficiency, scaling  
**Behavior:**
- Focus on automation and efficiency
- No-code / low-code thinking (Zapier, Make, etc.)
- Process optimization mindset
- Budget/resource management

#### Role 4: EdTech Specialist  
**Trigger:** School, teaching, classes, students, materials  
**Behavior:**
- Maximize student value, minimize prep time
- Suggest AI integration in teaching
- Focus on practical classroom use
- Consider different student levels

#### Role 5: Life Coach (Analytical)  
**Trigger:** Personal topics, health, time management, balance  
**Behavior:**
- Fact-based advice (no fluff)
- Time management with realistic constraints
- Balance: work + IT study + family + rugby
- Direct about sustainability

---

## Layer 3: Memory System

Memory is **not** automatic. It's written only when you explicitly ask:
- "Remember that..."
- "Don't forget..."
- "Make a note..."
- "Zapomeň si..."

### How Memory Works

When you write to memory, it's stored as:
```
[Topic]: [Detailed fact or learning]
```

### Example 1: School Context

```
You: "Vytvoř test pro žáky 7.A v rámci základní školy na savce na základě vložených podkladů."

Claude thinks:
  1. Checks context: "This is education question"
  2. Activates: role_education (EdTech Specialist mode)
  3. Reads memory: "7.A has 25 students, Krejčí needs simple texts"
  4. Reads instructions: "Maximize value, minimize prep time"

Output:
  - Test with two difficulty levels
  - Simple version for Krejčí + friends
  - Advanced version for Svobodová (ready for challenge)
  - Includes QR codes to video explanations
  - Designed for 45-min lesson
```

---

### 3. Role Clarity

Each role has:
- Clear trigger (what activates it)
- Clear behavior (how it changes response)
- Clear scope (what it applies to)

### 4. Explicit Context Switching

Claude doesn't guess. It checks:
1. Is this IT, career, business, education, or personal?
2. Which role applies?
3. What does memory say about this?
4. What does the communication style guide say?

---

## vs. Cowork OS (Local System)

| Aspect | Claude Projects | Cowork OS |
|---|---|---|
| **Storage** | Cloud | Local files |
| **Accessibility** | Web only | Desktop + web |
| **Version Control** | None | Full git history |
| **Structure** | Flat (one project) | Hierarchical (folders) |
| **Memory Format** | Proprietary | Markdown (.md) |
| **Offline** | No | Yes |
| **Setup** | Instant | Requires folder + files |
| **Multi-project** | Create separate projects | One folder, many subfolders |

**When to use Claude Projects:**
- Need instant, accessible workspace
- Working solo (don't need version history)
- Want simple role-switching
- Don't need filesystem integration

**When to use Cowork OS:**
- Need project hierarchy (Škola, Rugby Plus, Automation, etc.)
- Want version control on instructions/memory
- Need live data connectors
- Want repeatable skills/workflows

---

## How to Build This for Yourself

### Step 1: Create Project
Go to claude.ai → Projects → New Project  
Name it something meaningful

### Step 2: Define Personal Context
Write structured XML/markdown covering:
- Who you are
- What you do
- What you know
- What you want

### Step 3: Define Roles
For each major context, write role definition:
```
<role_[name]>
  Trigger: [When does this activate]
  Behavior: [How do I change]
  Scope: [What does this apply to]
</role_[name]>
```

### Step 4: Set Communication Style
Be explicit about:
- Tone (formal? casual? direct?)
- Level (assume what knowledge?)
- Format (prose? lists? code blocks?)
- What bothers you (filler? over-explanation?)

### Step 5: Use Memory Intentionally
Don't write generic memory.  
Write specific facts that change how Claude helps you.

---

## Future Improvements

- [ ] Export memory to markdown (backup, portability)
- [ ] Integrate with Cowork OS (sync memory between systems)
- [ ] Add more specialized roles and plugins (e.g., writer, storyteller)
- [ ] Create role-specific prompts (advanced users)
- [ ] Version history for custom instructions (see what changed)

---

