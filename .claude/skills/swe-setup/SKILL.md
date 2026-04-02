---
description: Interactive setup to populate KB sections for SWE dual-persona resumes
user-invocable: true
---

# /swe-setup

**User input:** `$ARGUMENTS`

Parse `$ARGUMENTS`:
- Empty → full setup (all phases)
- Phase number (e.g., `2`) → resume from that phase
- "status" → show what's built vs missing

---

## Startup

1. Read `CLAUDE.md` — check KB Corrections Log
2. Read `config.md` — check if already partially filled
3. Scan `resume_builder/experience/` and `resume_builder/projects/` — see what's already built
4. Determine which phase to start from (or do full setup)

**Progress:** "Starting SWE setup wizard..."

---

## Phase 1: Seed config.md (Personal Info + Role Types)

**Goal:** Collect basic info and establish the two personas.

**Questions for user:**

1. **Personal Info:**
   - Full name?
   - Email address?
   - Phone number?
   - City, State, ZIP?
   - LinkedIn URL? (optional)
   - GitHub URL? (recommended)
   - Website/portfolio? (optional)

2. **Role Types — Define your two personas:**
   - **Persona 1 — DevOps/SRE/Cloud:**
     - Ask: "Which companies/roles target this? (examples: AWS, Google Cloud, Stripe Platform, Cloudflare)"
     - Confirm: "Tier 1 (strongest evidence) or Tier 2 (with targeted emphasis)?"

   - **Persona 2 — FullStack/SWE:**
     - Ask: "Which companies/roles target this? (examples: startups, FAANG product teams, Discord)"
     - Confirm: "Tier 1 or Tier 2?"

3. **Role-Type Decision Tree:**
   - Ask user to add 1-2 keyword mappings:
     - "If a JD mentions ___ keywords, which persona should I default to?"
     - Example: "Kubernetes + Terraform → DevOps/SRE" or "React + API design → FullStack/SWE"

4. **Write to config.md:**
   - Fill Personal Info section
   - Fill Role Types table (DevOps/SRE and FullStack/SWE rows)
   - Fill Role-Type Decision Tree with 3-4 mapping rows

**MANDATORY STOP:**
Show the filled config.md preview. Ask: "Does this look right? Any corrections?"
Wait for user confirmation before proceeding.

---

## Phase 2: Build Experience Files (Two Variants Per Position)

**Goal:** Capture work achievements, framed for both personas.

**Setup:**
- Ask: "How many positions (internships/jobs) do you want to include? (most recent first)"
- For each position, ask:
  - Company name?
  - Job title?
  - Start and end dates?
  - Brief description (1 sentence)?

**For each position:**

1. **Collect Achievements:**
   - "List 5-8 key accomplishments from this role."
   - For each achievement, ask:
     - What did you build, ship, or improve?
     - What was the outcome/metric? (latency, users, uptime, deploy frequency, etc.)
     - Did you lead, contribute, or support? (ownership level)

2. **Dual-Frame Each Achievement:**
   - "Reframe for DevOps/SRE angle: Which of these relate to reliability, automation, infrastructure, or on-call?"
   - "Reframe for FullStack/SWE angle: Which relate to shipping features, system design, product impact, or APIs?"

3. **Write Experience Files:**
   - For DevOps angle: `resume_builder/experience/experience_<company>_devops.md`
   - For FullStack angle: `resume_builder/experience/experience_<company>_swe.md`

**Achievement Entry Format (in each file):**

```markdown
### [ID]: Achievement Name
**Context:** [1 sentence — what problem / why it mattered]
**Tech:** [tools, languages, frameworks used]
**Quantitative:** [verified metrics — latency reduced, uptime %, users served, deploy frequency]
**Bullet (2L) [DevOps frame]:** [LaTeX bullet — emphasize reliability/automation/infra angle]
**Bullet (2L) [SWE frame]:** [LaTeX bullet — emphasize shipping/product/design angle]
**Bullet (1L) [tight budget]:** [condensed version for 1-page]
**Tags:** devops, swe, cloud, backend, frontend, databases, etc.
**Significance (DevOps):** [one line — why this matters to SRE hiring manager]
**Significance (SWE):** [one line — why this matters to product/backend hiring manager]
```

**Example Achievement:**

```markdown
### E1: Deployment Pipeline Automation
**Context:** The team was manually deploying code, causing long release cycles and human errors.
**Tech:** GitHub Actions, Docker, Terraform, AWS
**Quantitative:** Reduced deployment time from 45 min to 8 min. Enabled 20+ deploys/day.
**Bullet (2L) [DevOps frame]:** Architected CI/CD pipeline using GitHub Actions + Terraform, reducing deployment time 82% and enabling canary-based rollouts with automated rollback.
**Bullet (2L) [SWE frame]:** Shipped end-to-end CI/CD system enabling 20+ daily deployments with zero-downtime releases to 500k+ users.
**Bullet (1L) [tight budget]:** Built CI/CD pipeline reducing deploy time 45min → 8min; enabled daily releases.
**Tags:** cicd, devops, automation, infrastructure, shipping
**Significance (DevOps):** Shows infrastructure automation at scale, MTTR improvement, ownership of deployment reliability.
**Significance (SWE):** Shows ownership of shipping infrastructure, enabling product velocity, system design thinking.
```

**MANDATORY STOP after Phase 2:**
Show: "I've built experience files for [N] positions with [M] achievements each, in DevOps and FullStack variants."
Ask: "Any achievements missing? Any metrics wrong?"
Wait for confirmation before continuing to Phase 3.

---

## Phase 3: Build Projects Pool

**Goal:** Capture side projects, hackathons, open-source, personal projects.

**Questions:**

1. "How many projects do you want to include in your pool? (5-10 recommended)"
2. For each project:
   - Project name?
   - Tech stack? (languages, frameworks, infrastructure)
   - What year(s)? (single year or range)
   - What does it do? (1-2 sentences, plain English)
   - Any metrics? (GitHub stars, users, performance, scale)
   - GitHub/demo link? (optional but valuable)
   - Which SWE domain keywords does it touch? (kubernetes, react, python, api, databases, etc.)

**Write Project Files:**

For each project: `resume_builder/projects/project_<slug>.md`

**Project Card Format:**

```markdown
# Project: [Name]

## Overview
- **Year:** [YYYY or YYYY-YYYY if range]
- **Type:** [Personal | Coursework | Open-Source | Hackathon | Work]
- **Status:** [Active | Archived | In Development]
- **Repo/Demo:** [URL or "private"]

## Stack
- **Languages:** [e.g., Python, TypeScript]
- **Frameworks:** [e.g., FastAPI, React]
- **Infrastructure:** [e.g., AWS EC2, Docker, Redis]
- **Other:** [e.g., PostgreSQL, GitHub Actions]

## What It Does
[1-2 sentence description — plain language, not resume prose]

## Quantitative
[Any metrics: users, requests/sec, size in KB, GitHub stars, uptime, latency improvements, etc. — verified facts only]

## Bullets

### DevOps/Infra Frame (use when JD is DevOps/SRE/Platform)
**Bullet (2L):** [LaTeX bullet emphasizing infra/reliability/scale angle]
**Bullet (1L):** [condensed version]

### FullStack/Product Frame (use when JD is SWE/FullStack/Backend)
**Bullet (2L):** [LaTeX bullet emphasizing features/system design/product angle]
**Bullet (1L):** [condensed version]

## Tags
[comma-separated keywords: kubernetes, cicd, react, typescript, postgresql, aws, etc.]
```

**Example Project:**

```markdown
# Project: Distributed Cache Library

## Overview
- **Year:** 2023-2024
- **Type:** Personal
- **Status:** Active
- **Repo:** github.com/yourname/dist-cache

## Stack
- **Languages:** Go, Rust
- **Frameworks:** gRPC
- **Infrastructure:** Docker, Kubernetes

## What It Does
A distributed caching library written in Go with optional Rust acceleration for low-latency environments. Supports multi-node clusters with automatic failover.

## Quantitative
- 500+ GitHub stars
- Handles 1M+ requests/sec per node
- <5ms p99 latency
- 99.99% uptime in production clusters

## Bullets

### DevOps/Infra Frame
**Bullet (2L):** Built distributed caching system handling 1M+ RPS with 99.99% uptime and <5ms p99 latency; deployed across 8 Kubernetes clusters.
**Bullet (1L):** Designed HA caching system: 1M RPS, <5ms latency, 99.99% uptime.

### FullStack/Product Frame
**Bullet (2L):** Engineered distributed cache library enabling 40% reduction in database queries for downstream services; 500+ GitHub stars.
**Bullet (1L):** Built caching library reducing DB load by 40%; shipped to production.

## Tags
kubernetes, go, distributed-systems, performance, infrastructure, cache, open-source
```

**MANDATORY STOP after Phase 3:**
Show: "I've created [N] project cards in your pool."
Ask: "Any projects missing? Any metrics wrong?"
Confirm before proceeding to Phase 4.

---

## Phase 4: Build Bundles + Skills Guide

**Goal:** Synthesize experience files and project pool into strategic bundles and skills taxonomy.

**Actions (Claude performs, user confirms):**

1. **Read all experience files** (both DevOps and SWE variants)
2. **Extract all skills** mentioned in Tech fields → build skills_guide.md
3. **Create bundle_devops_sre.md:**
   - S1: Role Profile — DevOps/SRE target roles and what they value
   - S2: Summary Guide — DevOps tagline patterns
   - S3: Reframing Map — priority matrix for DevOps achievements
   - S4: Skills Guide — DevOps skills to emphasize + group order
   - S5: CL Guide — Cover Letter hooks for DevOps/Platform roles

4. **Create bundle_fullstack_swe.md:**
   - S1: Role Profile — FullStack/SWE target roles and what they value
   - S2: Summary Guide — FullStack tagline patterns
   - S3: Reframing Map — priority matrix for SWE achievements
   - S4: Skills Guide — SWE skills to emphasize + group order
   - S5: CL Guide — Cover Letter hooks for product/SWE roles

5. **Create skills_guide.md:**
   - Aggregate all languages, frameworks, tools from experience + projects
   - Organize by proficiency: Expert | Proficient | Familiar
   - Map to evidence (which position/project demonstrates each skill)

**Final Status Report:**

```
✅ Knowledge Base Built!

Experience Files:
  - experience_company1_devops.md (5 achievements)
  - experience_company1_swe.md (5 achievements)
  - experience_company2_devops.md (4 achievements)
  - experience_company2_swe.md (4 achievements)

Projects Pool:
  - 8 project cards, scored and ready for JD matching

Bundles:
  - bundle_devops_sre.md (S1–S5, ready for /make-resume)
  - bundle_fullstack_swe.md (S1–S5, ready for /make-resume)

Skills:
  - skills_guide.md (aggregate of all technical skills with evidence)

Next Steps:
1. Run: /make-resume JDs/your_target_job.txt
2. Persona will auto-detect (DevOps vs FullStack)
3. Projects will auto-score and select by JD relevance
4. Resume will generate with persona-specific bullets and projects
```

**FINAL MANDATORY STOP:**
Ask: "Knowledge base is ready! Do you want to:"
- Option 1: Start with `/make-resume` (I'll show you how to use it)
- Option 2: Review/edit the KB files you just created
- Option 3: Exit and refine later

---

## Error Handling

If user provides incomplete data:
- "I need a metric for this achievement (latency, users, uptime, etc.) to make it memorable. Can you estimate?"
- "This tech stack seems sparse. Did you miss any frameworks or databases?"
- If projects lack GitHub/demo links: "No problem — I'll mark this as 'private' and it'll score lower on JD relevance, which is fair."

---

## Notes for Claude (Implementation)

- Use LaTeX-ready bullet templates; validate char counts with `char_count.py` BEFORE writing to files
- Build all files incrementally; save to disk as you go (don't wait until end)
- When extracting skills for skills_guide.md, de-duplicate and organize by category (Languages, Frameworks, Infrastructure, Testing, etc.)
- For bundles, use the user's own achievements as examples in the Reframing Maps — personalized bundles > generic templates
- Validate that every achievement has both DevOps and SWE framings before marking Phase 2 done
- If user skips a phase or chooses to resume: reload state from disk and continue from that phase without repetition
