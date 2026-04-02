---
description: Generate a tailored resume/CV from a JD
user-invocable: true
---

# /make-resume

**User input:** `$ARGUMENTS`

Parse `$ARGUMENTS`:
- File path (e.g., `JDs/*.txt`) → read that file for the JD
- Text after the path starting with "Focus:"/"Emphasize:"/"Downplay:" → focus directive
- "Quick:" prefix → Quick Mode (see below)
- Empty → ask the user for the JD
- Inline JD text (no file path) → save to `JDs/temp_<company>.txt`, proceed normally

---

## Safety Rules (ALWAYS ENFORCED)

**Accuracy > Relevance > Impact > ATS > Brevity**

Read `config.md` Provenance Flags before generating any content. Verify every claim against that table.

- Use the email from `config.md` Personal Info in all outputs
- Resume bullets: ALL variable bullets are 2L (CV: 2L/3L mix OK, check `config.md` Document Preferences)
- Source ALL bullet content from `resume_builder/experience/` files. Never fabricate.
- Run `python3 resume_builder/helpers/char_count.py` after each section — the tool is authoritative

---

## User Input During Execution

If the user provides feedback, corrections, or suggestions at any point:
1. Acknowledge the input immediately
2. If it affects an already-written section: go back, fix it, re-run char count gate
3. If it changes the bullet plan: update session file Bullet Plan
4. If it's a question: answer it, then continue from current step
5. Never restart a phase — resume from current position

---

## Startup

Read `resume_builder/reference/shared_ops.md` for session startup, file derivation, and organization protocols.

Then:
1. Read `CLAUDE.md` — check Active Sessions and KB Corrections
2. Read `config.md` — load Provenance Flags, email, document preferences, role types
3. If session file exists for this JD:
   - Read session file, check Status
   - Phase 0: DONE, Phase 1: PENDING → resume at Phase 1 (skip persona detection)
   - Phase 1: DONE → resume at Budget Gate
   - Phase 2: IN_PROGRESS → read .tex, check what sections exist, resume from checkpoint
   - Phase 2: DONE → "Resume already done. Run /make-cl next." Show next command. Stop.
4. If no session file: proceed to Persona Detection

---

## Persona Detection (BEFORE Phase 0)

**Only runs if session file does NOT exist (new JD).**

**Purpose:** Automatically detect whether this JD is DevOps/SRE or FullStack/SWE. This determines which experience files and bundle are loaded.

**Method:** Score JD keywords against signal sets. Higher count wins; within 20% = Hybrid.

**Signal Sets:**

DevOps/SRE signals (prioritize infrastructure, reliability, scale, automation):
- Keywords: Kubernetes, Terraform, Docker, AWS, GCP, Azure, Helm, Ansible, CI/CD, Prometheus, Grafana, SRE, "reliability", "on-call", "infrastructure as code", "deployment", "scaling", "uptime"

FullStack/SWE signals (prioritize shipping, product, APIs, system design):
- Keywords: React, TypeScript, Node.js, Python, Go, Java, REST API, GraphQL, "backend", "system design", "microservices", "feature", "API design", "product", SQL, database design

**Scoring:**
1. Tokenize JD into lowercase words
2. Count DevOps signal matches
3. Count SWE signal matches
4. Determine persona: DevOps if higher count, SWE if higher count, Hybrid if within 20%
5. Store in session file (will be written in Phase 0)

**Output:** `Persona: DevOps/SRE | FullStack/SWE | Hybrid (Primary: DevOps | Primary: SWE)`

Progress: "Analyzing JD keywords..." / "Detected: [Persona] (DevOps signals: N, SWE signals: M)"

---

## Quick Mode

Trigger: `$ARGUMENTS` starts with "Quick:"

Defaults:
- Detect persona from JD keywords (auto-pass persona confirmation)
- Select all HIGH priority achievements from bundle's Priority Matrix as 2L
- Fill remaining budget with MEDIUM priority in Priority Matrix order
- Default format: 1-page resume (SWE focus)
- Auto-select top 2 projects by JD keyword score
- Skip Phase 0 STOP and Phase 1 STOP
- Keep Budget Gate (auto-pass if within target) and end-of-resume STOP
- Run all phases with progress commentary instead of interactive stops

---

## Phase 0: Research & Session Setup

**Read these files:**
1. The JD (from `$ARGUMENTS`)
2. `resume_builder/reference/resume_reference.md` — Budget Card, Section Specs, Char Limits, Page Budgets
3. `config.md` — Role-Type Decision Tree to identify the matching bundle

**Web Search (MANDATORY — 2-3 searches).** Load WebSearch via ToolSearch first.
1. `[Company] research & development [key JD domain]` — products, recent projects
2. `[Company] [specific technology from JD]` — concrete hooks for cover letter
3. `[Company] careers [role type] culture` OR recent news — hiring context

If web search returns no results: use JD text + training knowledge. Flag: "Web search returned limited results — CL hooks may be generic."

**Produce all of these (reference `resume_builder/reference/session_file_template.md` for format):**
- **JD Analysis** — classify every requirement as Direct / Bridge (with confidence) / Gap. Extract ATS keywords by category.
- **Company Context** — mission, role purpose, culture signals, "why them" angle (from web research)
- **Framing Strategy** — lead narrative, reframing map, emphasize/downplay, CL hooks, user focus directives
- **Critique Context** — reviewer persona, competitive landscape, domain vocabulary
- **Cover Letter Plan** — institution type, paragraph structure, hooks, jargon level

**Create output folder:**
Derive folder name from JD filename: `JDs/JD_Acme.txt` → `output/Acme/`
```bash
mkdir -p output/<FolderName>/
```
Write session file to `output/<FolderName>/session_<name>.md` (NOT flat `output/`).
All subsequent output files go in this folder.

**Add Persona to session file:**
- Write the detected persona (from Persona Detection section) to session file under `**Persona:**`
- If persona is Hybrid: ask which should be primary (or let user decide later)

**Verify completeness:** Re-read the session file. Confirm these 9 sections are non-empty: Persona, JD Info, Requirements table, ATS Keywords, Gap Assessment, Company Context, Framing Strategy, Critique Context, Cover Letter Plan. Fill any missing section before presenting.

**Write memory pointer** to `CLAUDE.md` Active Sessions.

**Update session file Status:** `Phase 0: DONE`

Progress: "Searching for [company] + [domain]..." / "JD analysis: X/Y requirements direct match, Z bridges, W gaps" / "Persona detected: [DevOps/SWE]"

### >>>>>> MANDATORY STOP — DO NOT PROCEED <<<<<<
Present: research summary, detected persona, role type + bundle, format, framing strategy.
Ask user to confirm: (1) detected persona (OK / change to other), (2) role type + bundle, (3) format, (4) framing strategy.
**You MUST wait for the user's explicit text response before continuing.**
Proceeding without confirmation misaligns the entire resume and requires full regeneration.

---

## Phase 1: Plan Bullets & Projects

**Re-read `output/<FolderName>/session_<name>.md`** — specifically Persona, Framing Strategy, and ATS Keywords.

**Read:**
1. The matching bundle from Persona → `resume_builder/bundles/bundle_devops_sre.md` OR `bundle_fullstack_swe.md` — Section 1 (Priority Matrix)
   - For hybrid JDs: read both bundles. Use primary for Priority Matrix, secondary for Reframing Map on 1-2 bridging bullets.
2. Persona-specific experience files from `resume_builder/experience/`:
   - If Persona = DevOps/SRE: read `experience_*_devops.md` files
   - If Persona = FullStack/SWE: read `experience_*_swe.md` files
   - If Persona = Hybrid: read both variants, use primary persona for primary bullets, secondary for bridges
3. `resume_builder/support/skills_guide.md`

**Experience Bullets Table — Present one table per position:**

**[Position Name] (Budget: N-M bullets, ~X-Y rendered lines)**

| | ID | Achievement | Variant | Lines | JD Match |
|---|---|-------------|---------|-------|----------|
| * | P1-1 | [short description] | 2L | 2 | Direct |
| * | P1-5 | [short description] | 2L | 2 | Direct |
| o | P1-3 | [short description] | 2L | 2 | Bridge |
| x | P1-7 | [short description] | -- | -- | Weak |

**Legend:** `*` = recommended (HIGH on Priority Matrix + Direct JD match) | `o` = available (MEDIUM priority or Bridge match) | `x` = not recommended (LOW priority or Gap)

**After all positions, show:**
- Recommended set total vs budget (from Quick Budget Card in resume_reference.md)
- Remaining budget slots and what could fill them
- Forced exclusions per provenance flags
- Focus directive impact (what changed vs Priority Matrix defaults)

**Project Scoring & Selection**

Read all project files from `resume_builder/projects/project_*.md`.

For each project, score against JD ATS Keywords:
- Extract Tags from project file
- Count overlaps with ATS Keywords from session file (extract from Phase 0)
- Assign score: HIGH (5+ matches), MEDIUM (2–4 matches), LOW (<2 matches)

**Present project scoring table:**

| Score | Project Name | Tags | Matches | Justification |
|-------|--------------|------|---------|---------------|
| HIGH | [Project A] | [tags] | [N keywords matched] | [reason] |
| MEDIUM | [Project B] | [tags] | [N] | [reason] |
| LOW | [Project C] | [tags] | [N] | [reason] |

Default selection: Top 2 projects by score (or top 3 if budget allows for Projects section).

**Update session file:**
- Write Bullet Plan tables for experience
- Write Projects Scoring table with confirmed project selection

Status: `Phase 1: DONE (N bullets confirmed, M projects selected)`

Progress: "Reading experience files for bullet candidates..." / "Recommending N bullets per position" / "Scoring projects by JD keyword overlap..."

### >>>>>> MANDATORY STOP — DO NOT PROCEED <<<<<<
Present bullet plan + project selection. Wait for user to confirm/modify selections.
**You MUST wait for the user's explicit text response before continuing.**
If you proceed without confirmation, you will generate bullets and projects the user didn't approve.
**Update session file with confirmed plan before continuing.**

---

## Budget Gate (AFTER user confirms bullet plan, BEFORE Phase 2)

**Re-read session file Bullet Plan section** to verify confirmed counts.

- Check budget targets from `resume_builder/reference/resume_reference.md` Budget Card.
- Show: `Budget: [N] bullets vs target [T]. PASS/FAIL`
- **FAIL = do not proceed. Reconcile with user first.**

---

## Phase 2: Generate

**Re-read to restore context after compaction:**
1. `output/<FolderName>/session_<name>.md` (framing + confirmed bullet plan)
2. `resume_builder/reference/critical_rules.md` — Character Limits, Bold Width Penalty, Orphan rules
3. `resume_builder/support/ai_fingerprint_rules.md` — Banned words, structural rules, post-gen checklist

**Read template:** `resume_builder/templates/resume_template.tex` or `cv_template.tex` + `.cls`
FIXED sections (from `config.md` FIXED Sections) are template-locked — only generate VARIABLE sections (Summary, Skills, Experience bullets/headers).

**Read section specs:** `resume_builder/reference/resume_reference.md` — Section-by-Section Specs for your format

**Generate section by section** (follow Section-by-Section Specs):
1. Summary → check against session framing strategy
   - Update Status → `Phase 2: Summary DONE`
2. Technical Skills
   - Update Status → `Phase 2: Skills DONE`
3. Each position's bullets → **CHAR COUNT GATE after each position**
   - Position titles: bold theme + date must fit ONE line (see resume_reference.md). If wrapping, shorten title.
   - After each position: Update Status → `Phase 2: [Position] DONE`
4. **PAGE FILL GATE after all experience**
5. Projects section (new) → **CHAR COUNT GATE after projects**
   - Read confirmed project selection from session file
   - For each project: use persona-matching bullet variant (DevOps frame if DevOps persona, SWE frame if SWE)
   - Project header: name + year + stack (max 1 line)
   - 1–2 bullets per project (max 2L each)
   - After all projects: Update Status → `Phase 2: Projects DONE`
6. **Education + Awards** — FIXED sections (copy from config.md FIXED Sections)

Save .tex to `output/<FolderName>/e2e_<name>_resume.tex`

**Update session file** — add Output Files.

Progress: "Writing Position 1 bullets (6 of 7)..." / "Bullet 4 is SHORT at 184 chars — padding" / "Compiling resume... 2 pages OK"

### CHAR COUNT GATE (per position)
```bash
python3 resume_builder/helpers/char_count.py -f [resume|cv] output/<FolderName>/[file].tex
```
No OVER violations. Last line of 2L bullets >= 70% fill. **Fix before next position.**

### PAGE FILL GATE
Resume: <= 3 lines white space on last page. CV: check rendered line target from resume_reference.md. **If FAIL: add/trim variable bullets.**

### COMPILE GATE
```bash
pdflatex -interaction=nonstopmode -output-directory=output/<FolderName> output/<FolderName>/e2e_<name>_resume.tex
```
Verify page counts match `config.md` Document Preferences. Use the Read tool to view compiled PDF — check orphans, header wrapping, page fill. **If FAIL: fix variable content, recompile.**

Run the Post-Generation Verification checklist from `resume_builder/reference/resume_reference.md` before proceeding.

Update Status → `Phase 2: Compile DONE`

---

## End of /make-resume

Update session file Status:
- `Resume: DONE (Experience + Projects + Education)`
- `Cover Letter: PENDING`
- `Critique: PENDING`
- `Next: /make-cl output/<FolderName>/session_<name>.md`
- `Next Critique: /critique output/<FolderName>/session_<name>.md`

### >>>>>> MANDATORY STOP <<<<<<
Present: resume compilation summary (pages, char count results, any violations fixed, projects included).
**You MUST wait for the user's explicit text response before continuing.**

"Resume compiled and verified. Sections: Summary + Skills + Experience (N positions, M bullets) + Projects (K projects, L bullets) + Education/Awards.

Next steps:
1. /clear
2. [exact /make-cl command with session file path]"
