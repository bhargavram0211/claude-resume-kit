# Documentation

Detailed reference for claude-resume-kit. For the quick overview, see [README.md](README.md).

---

## Architecture

```
claude-resume-kit/
├── CLAUDE.md                          # Auto-loaded project instructions
├── config.md                          # Your personal configuration
├── .claude/skills/                    # 6 skills (invoked as /skill-name)
│   ├── setup-extract/SKILL.md         # Extract from papers → structured data
│   ├── setup-build-kb/SKILL.md        # Synthesize KB from extractions
│   ├── make-resume/SKILL.md           # JD → tailored resume/CV (.tex)
│   ├── make-cl/SKILL.md              # Session → cover letter (.tex)
│   ├── edit-resume/SKILL.md           # Edit from critique/feedback
│   └── critique/SKILL.md             # Independent quality review
├── resume_builder/
│   ├── reference/                     # Generation rules and protocols
│   │   ├── shared_ops.md              # Session workflow (all skills read this)
│   │   ├── resume_reference.md        # Resume/CV formatting rules
│   │   ├── cl_reference.md            # Cover letter rules
│   │   ├── critical_rules.md          # Compact re-read for generation phase
│   │   ├── session_file_template.md   # Session file format spec
│   │   └── critique_framework.md      # 8-part critique system
│   ├── templates/                     # LaTeX .cls classes + .tex templates
│   │   ├── resume.cls                 # 2-page resume class
│   │   ├── cv.cls                     # Multi-page CV class
│   │   ├── resume_template.tex        # Resume structural template
│   │   ├── cv_template.tex            # CV structural template
│   │   └── coverletter_template.tex   # Cover letter template
│   ├── helpers/
│   │   └── char_count.py              # Character counting utility for bullets
│   ├── examples/                      # Fictional "Dr. Jordan Chen" — full worked example
│   ├── experience/                    # YOUR experience files (built by /setup-build-kb)
│   ├── bundles/                       # YOUR role-type bundles (built by /setup-build-kb)
│   └── support/                       # Skills taxonomy, pub metadata, AI fingerprint rules
├── knowledge_base/
│   ├── extractions/                   # Paper extractions (built by /setup-extract)
│   ├── papers/                        # Drop your PDFs / .tex source here
│   └── notes/                         # Any other reference material
├── JDs/                               # Job descriptions (text files)
└── output/                            # Generated .tex files, session files, critiques
```

---

## Use Cases: Researchers vs. Software Engineers

This kit supports two distinct workflows:

### Researchers (PhDs, Faculty Candidates)
- **Setup:** Extract papers (PDF or LaTeX source) using `/setup-extract`
- **Knowledge Base:** Extractions → experience files (with publication status) → bundles (Academic, R&D, Startup)
- **Resume:** 2–5 page CV with tailored bullets, publications, funding, awards
- **Skills:** Paper extraction, publication framing, multi-audience positioning (tenure-track, postdoc, industry)

### Software Engineers (Students, IC Track, Career-Changers)
- **Setup:** Structured Q&A using `/swe-setup` to capture positions and projects
- **Knowledge Base:** Work history + projects → dual-persona experience files (DevOps/SRE variant + FullStack/SWE variant) + bundles + projects pool
- **Resume:** 1-page resume with persona-specific bullets and auto-selected projects
- **Skills:** Dual-persona framing, JD keyword detection, project relevance scoring, role-type auto-detection

Both tracks use the same generation pipeline (`/make-resume`, `/make-cl`, `/critique`, `/edit-resume`).

---

## Concepts

### Session Files

Every JD gets a session file (`output/<Folder>/session_<name>.md`) that tracks:
- JD analysis and ATS keywords
- Which bundle was selected
- Bullet plan (which achievements, in what order, at what length)
- All generation decisions and their rationale
- Cover letter plan
- Critique scores

All 4 generation skills read and update this file. It's the single source of truth for each application.

### Experience Files

One file per position (e.g., `experience_postdoc_university.md`). Each achievement has:
- **Source paper** with citation
- **Methods and tools** used
- **Quantitative results**
- **Pre-written bullet variants** (2-line and 3-line)
- **Tags** for which role types this achievement is relevant to
- **Significance** context for cover letters

### Role-Type Bundles

One file per target audience (e.g., `bundle_academic.md`). Each bundle contains:
- **S1: Role Profile** — what this audience values, positioning strategy
- **S2: Summary Guide** — how to write the summary for this role type
- **S3: Achievement Reframing Map** — priority ranking of your achievements for this audience
- **S4: Skills Guide** — which tools to bold, which to include, grouping strategy
- **S5: Cover Letter Guide** — opening hooks, paragraph templates, anti-patterns

### Provenance Flags

The system enforces accuracy through provenance tracking in `config.md`. Every achievement is tagged with its publication status. The skills check this table before every output and will never:
- Claim unpublished work is published
- Claim internal tools are peer-reviewed
- Use full-ownership verbs for shared work
- Inflate author position

### SWE-Specific Concepts (Dual-Persona Framework)

**Personas:** The system supports two distinct role types:
- **DevOps/SRE/Cloud/Infrastructure** — reliability, automation, scale, on-call culture, infrastructure as code
- **FullStack/SWE/Product** — shipping, system design, API design, product impact, technical ownership

**Experience Variants:** Each position has two framings:
- `experience_<company>_devops.md` — same achievements, framed for infrastructure impact (uptime, deployments, scaling, MTTR)
- `experience_<company>_swe.md` — same achievements, framed for product impact (features shipped, system design, user velocity)

**Persona Detection:** When you run `/make-resume` on a JD, the system automatically scores DevOps vs SWE keywords:
- DevOps signals: Kubernetes, Terraform, SRE, reliability, on-call, infrastructure as code, deployment, scaling, uptime
- SWE signals: React, TypeScript, Node.js, backend, system design, feature, API, microservices, product

Higher score = detected persona. Matched bullets are pulled from the corresponding experience variant.

**Projects Pool:** One central directory (`resume_builder/projects/`) holds all projects. Each project card has:
- Dual bullet variants (DevOps frame + SWE frame)
- Tags for JD keyword matching
- Metrics (GitHub stars, production scale, latency, throughput)

During generation, projects are scored by JD keyword overlap and auto-selected (top 2–3 by score).

**Role-Type Bundles:** Two bundles encode role-type strategy:
- `bundle_devops_sre.md` — S1–S5 for infrastructure roles (role profile, summary tagline, achievement reframing, skills grouping, CL hooks)
- `bundle_fullstack_swe.md` — S1–S5 for product/SWE roles

The detected persona determines which bundle is loaded for that JD.

---

### The Critique System

The `/critique` skill runs a multi-part assessment:
1. **Domain-Specialist Lens** — reviewer persona, gap analysis, competitive landscape
2. **Five-Perspective Read-Through** — ATS bot, recruiter (10s), HR (30s), hiring manager (2min), technical reviewer (10min)
3. **Eight-Dimension Scoring** — weighted score out of 100
4. **Interview Likelihood** — per-reader probability estimates
5. **Tiered Improvements** — ranked by point impact
6. **Interview Bridge Points** — resume-to-interview talking points
7. **Cover Letter Critique** — 6 sub-checks (anti-patterns, tailoring, context-specific, ATS keywords, structural, package cohesion)
8. **Post-Generation Verification** — mechanical and content checklists including AI fingerprint scan

---

## Three-Session Workflow

For best results, use a **separate Claude Code session** for each step. This gives each skill fresh context, which produces better quality (especially for critique — you want fresh eyes, not the same context that generated the resume).

```
Session 1:  /make-resume JDs/job.txt     → resume/CV .tex
            /clear
Session 2:  /make-cl                      → cover letter .tex
            /clear
Session 3:  /critique                     → critique .md with score
            /clear
            /edit-resume                  → refined .tex (if needed)
```

---

## Customization

### Everything in `config.md` (edit directly)

| Setting | What it controls | Example |
|---------|-----------------|---------|
| **Personal Info** | Name, email, phone, links on all outputs | Your contact details |
| **Document Preferences** | Page counts, bullet line variants, skills layout | `Resume: 2 pages, CV: 5 pages` |
| **Provenance Flags** | What claims are safe to make | `ML paper: under review → never say "published"` |
| **Role Types** | Target audiences and their bundles | `Academic (Tier 1), Industry R&D (Tier 2)` |
| **Decision Tree** | How JD keywords map to role types | `"tenure-track" → Academic` |
| **FIXED Sections** | Template sections that never change per JD | `Education, Publications, Awards` |
| **Output Rules** | Package formats and constraints | `Resume: 2pg + 1pg CL = 3pg package` |
| **KB Corrections** | Errors to never re-introduce | `Spearman is 0.82, not 0.85` |

### LaTeX Templates (edit directly)

- **Fonts, colors, spacing** — modify `.cls` files
- **Section order** — reorder sections in `.tex` templates
- **FIXED content** — fill in education, awards, publications, header
- **Icons** — replace `GS.png` / `orcid.png` with your own
- **Page geometry** — adjust margins in `.cls` if needed

### Knowledge Base (built by skills, then editable)

#### For Researchers
| File | How to customize |
|------|-----------------|
| **Experience files** | Edit bullet text, add/remove achievements, adjust tags |
| **Bundles** | Change priority matrices, rewrite summary guides, add role types |
| **Skills taxonomy** | Add/remove skills, change groupings, adjust bold rules |
| **Pub metadata** | Update citation counts, add new publications |

#### For Software Engineers
| File | How to customize |
|------|-----------------|
| **Experience files** (dual variants) | Edit bullets, adjust DevOps vs SWE framing, add/remove achievements |
| **Projects pool** | Add projects, update metrics, adjust GitHub links and tech tags |
| **Bundles** (DevOps + SWE) | Change priority matrices, rewrite role profiles, adjust persona signals |
| **Skills guide** | Organize skills by proficiency, mark DevOps/SWE emphasis |

### Reference Docs (advanced)

| File | What you'd change |
|------|-------------------|
| `resume_reference.md` | Page budgets, character limits, section specs |
| `cl_reference.md` | Cover letter paragraph templates, word count targets |
| `critical_rules.md` | Generation-time rules tables |
| `critique_framework.md` | Scoring weights, critique dimensions |
| `shared_ops.md` | Session workflow, file derivation logic |

### Skill Prompts (advanced)

Each skill is a markdown file in `.claude/skills/<name>/SKILL.md`. You can:
- Add STOP points for more user control
- Change the number of web searches in Phase 0
- Adjust how many bullets per position
- Modify the critique scoring weights
- Add new skills for your workflow

---

## Key Design Decisions

- **Accuracy > Relevance > Impact > ATS > Brevity** — the priority hierarchy for every generation decision
- **LaTeX-only output** — Claude generates `.tex`, you compile locally. No formatting surprises.
- **FLIPPED position format** — the bold line under each position title is a JD-customized theme, not a generic description. This is the strongest tailoring lever.
- **Structured provenance** — every achievement is tracked from source paper through extraction to experience file to resume bullet
- **Character-precise budgets** — every bullet is calibrated to fit the template geometry, not "try to keep it short"
- **Session files as state** — all decisions for a JD live in one file. Skills can recover from interruptions.
- **Anti-fabrication by design** — provenance flags, verb discipline, and corrections logs prevent overclaiming even under pressure to impress
- **AI fingerprint avoidance** — a dedicated rules file is loaded by all generation and critique skills, covering banned words and phrases (with technical exceptions), structural anti-patterns, positive markers, and a 12-item post-generation checklist

---

## FAQ

**Q: Do I need to know LaTeX?**
No. Claude generates the `.tex` files. You just compile them (`pdflatex file.tex`). The templates handle all formatting.

**Q: How many papers should I extract?**
All papers where you're first author or co-first author, plus key contributing-author papers. Quality matters more than quantity — 5 well-extracted papers beat 20 shallow ones.

**Q: Can I use this for non-academic roles?**
Yes. The framework supports any role type — define them in `config.md`. Industry R&D, consulting, data science, and engineering roles all work. Just create appropriate bundles.

**Q: What if I don't have a Google Scholar / ORCID?**
Remove those lines from the templates. The framework adapts to what you have.

**Q: How do I update after publishing new papers?**
Run `/setup-extract` on the new paper, then update your experience file and bundles. Existing session files are not affected.

**Q: Can I use this with resume formats other than the included templates?**
Yes. The `.cls` files define the visual style. You can modify them or write your own. The skills generate content based on the template structure — update the `[GENERATE: ...]` and `[FIXED: ...]` markers in your template.

**Q: Can multiple people use the same kit?**
Each person needs their own clone with their own `config.md`, knowledge base, and templates. The framework itself is shared; the content is personal.

**Q: What Claude model should I use?**
The skills are designed for Claude's most capable models (Opus, Sonnet). Less capable models may skip steps or produce lower-quality output.

---

## FAQ — SWE / DevOps Track

**Q: What if I apply to both DevOps/SRE and SWE/Backend roles?**
This is exactly what the dual-persona system handles. During `/swe-setup`, you create two framing variants for each position. When you run `/make-resume` on a JD, the system auto-detects the persona and pulls the matching bullets. No manual reframing needed.

**Q: How do I add a new position to my KB?**
You can either:
1. Run `/swe-setup` again to add it to your KB
2. Manually create `experience_<company>_devops.md` and `experience_<company>_swe.md` files in `resume_builder/experience/`, following the achievement format from the examples

**Q: Can I include side projects and coursework?**
Yes. The `/swe-setup` wizard and projects pool are designed for this. Each project can be a personal project, hackathon, open-source, coursework, or work project — just tag it appropriately.

**Q: What if a JD mentions both DevOps and SWE keywords?**
The system detects this as a "Hybrid" persona. It will ask you which is primary and load both variants, prioritizing the primary. You can always override at the Phase 0 STOP.

**Q: How is persona detection calibrated?**
The keyword matching is tuned to common industry terminology. If a JD uses non-standard language, you can override the detected persona at Phase 0 and choose manually.

**Q: Should I include all my projects in the pool?**
Include 5–10 strong projects that you're confident defending in an interview. Include older projects if they're still relevant to your target roles. The system will score by JD keyword match, so only the most relevant 2–3 will appear in any given resume.

**Q: How do I update a project's metrics?**
Edit the `project_<slug>.md` file in `resume_builder/projects/` directly. Update GitHub stars, latency metrics, scale, whatever is most impressive and accurate. Re-run `/make-resume` on your JDs to refresh the scoring.
