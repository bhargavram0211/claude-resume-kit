# claude-resume-kit

Most AI resume tools work the same way: paste resume + paste JD, get a rewrite. They don't know which of your papers is published vs. under review. They don't know you only ran the simulations, not the experiments. They'll upgrade "contributed to" into "developed" without blinking.

This is different. You structure your work once — the system asks detailed questions about each achievement, publication status, and technical contribution. After that, every new application is just pointing it at a JD. It detects which role type you're applying for, picks the right achievements, frames them for that audience, enforces accuracy, and generates LaTeX you compile locally.

Built for researchers (PhDs, faculty candidates) and software engineers (students, mid-career, IC track) with lots of source material (papers, code, projects, professional experience) who apply to many positions across different employer types and role tracks.

---

## What makes this different

**Knowledge base, not a rewriter.** You extract once. Every application draws from verified source material — not a pasted resume that gets "improved."

**Anti-fabrication by design.** Provenance flags on every achievement (published / under review / internal). Verb discipline rules prevent overclaiming. A corrections log ensures fixed errors don't reappear.

**AI fingerprint avoidance.** Banned-word lists, structural anti-patterns, and a 12-item post-generation scan so output reads as human-written.

**Multi-perspective critique.** Five reader personas (ATS bot through technical reviewer) score your resume across 8 dimensions in a fresh context window.

**LaTeX output, locally compiled.** No data leaves your machine beyond the Claude Code conversation.

---

## Example Output

### For Researchers (Academic Track)
Dr. Jordan Chen, computational biologist, applying to a tenure-track faculty position:
- [Example Resume (PDF)](resume_builder/examples/example_resume.pdf) — 2-page resume with JD-tailored bullets, skills, and publications
- [Example Cover Letter (PDF)](resume_builder/examples/example_cover_letter.pdf) — 1-page academic cover letter with specific hooks
- [Example Session File](resume_builder/examples/example_session_file.md) — the decision log that produced this output

### For Software Engineers (SWE / DevOps Track)
Example experience files and project cards in `resume_builder/examples/{experience,projects}/` show how the system frames the same work differently for DevOps/SRE roles vs. FullStack/SWE roles — auto-detecting from the JD and selecting the matching bullet variants.

All example data is in `resume_builder/examples/` — config, experience (academic variant), bundles, and session file. For SWE examples, see the example_experience_swe.md and example_project.md files.

---

## What you actually do

### For Researchers (Academic Track)

**One-time setup (~10 min per paper):**
1. Drop your papers/reports into `knowledge_base/papers/`
2. Run `/setup-extract` on each — Claude reads it and asks you questions about your contributions and publication status
3. Run `/setup-build-kb` — synthesizes everything into your knowledge base

**Per application (~15-20 min):**
1. Drop the JD into `JDs/`
2. Run `/make-resume JDs/target_job.txt` — approve the bullet plan, get a `.tex` file
3. Run `/make-cl` for a cover letter
4. Run `/critique` for a scored review with specific fixes

### For Software Engineers (SWE / DevOps Track)

**One-time setup (~20-30 min):**
1. Run `/swe-setup` — interactive wizard to populate your knowledge base
   - Personal info (name, email, GitHub, LinkedIn, etc.)
   - Work experience (positions with achievements framed for both DevOps/SRE and FullStack/SWE roles)
   - Projects (personal, open-source, hackathon, coursework)
   - Builds two bundles (DevOps/SRE and FullStack/SWE) with role-specific framing strategies

**Per application (~15-20 min):**
1. Drop the JD into `JDs/`
2. Run `/make-resume JDs/target_job.txt` — detects role type (DevOps vs SWE), picks matching bullets, scores projects by relevance, generates `.tex`
3. Run `/make-cl` for a cover letter
4. Run `/critique` for a scored review with specific fixes

---

Each skill runs in a **separate Claude Code session** for best quality (fresh context = less bias).

---

## Prerequisites

- **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** CLI installed and authenticated
- **A LaTeX distribution** for compiling `.tex` to `.pdf` (e.g., [TeX Live](https://tug.org/texlive/), [MacTeX](https://tug.org/mactex/), [MiKTeX](https://miktex.org/))
- **Your research papers** or project documentation ready for extraction

---

## Try it first (5 minutes)

Want to see what it does before extracting your own papers? The repo includes a complete example knowledge base for a fictional researcher:

```bash
git clone https://github.com/ARPeeketi/claude-resume-kit.git
cd claude-resume-kit
claude
/make-resume JDs/example_jd.txt
```

This runs the full pipeline — JD analysis, bullet selection, LaTeX generation — using the included example data. No setup required.

---

## Full Setup

### 1. Clone and configure

```bash
git clone https://github.com/ARPeeketi/claude-resume-kit.git
cd claude-resume-kit
```

Edit `config.md` with your details (name, email, provenance flags, role types). See `resume_builder/examples/example_config.md` for a complete example.

### 2. Extract your papers

Place PDFs or `.tex` source files in `knowledge_base/papers/`, then:

```
/setup-extract knowledge_base/papers/my_paper.pdf
```

Claude reads the paper, asks clarifying questions about your contributions, and creates a structured extraction. Repeat for each paper.

### 3. Build your knowledge base

```
/setup-build-kb
```

This synthesizes all extractions into experience files, role-type bundles, and support files.

### 4. Customize your LaTeX templates

Open the templates in `resume_builder/templates/` and fill in your FIXED sections — education, header, awards, publications. The `[CONFIG: ...]` placeholders show you what to fill in.

### 5. Generate for a job

```
/make-resume JDs/target_job.txt
```

Then in separate sessions: `/make-cl` for the cover letter, `/critique` for a scored review.

---

## How It Works

### Academic (Researcher) Pipeline
```
Your Papers --> /setup-extract --> Extractions --> /setup-build-kb --> Knowledge Base
                                                                          |
Job Description --> /make-resume --> Tailored Resume/CV (.tex)            |
                        |              v                                  |
                   /make-cl --> Cover Letter (.tex)                       |
                        |              v                                  |
                   /critique --> 8-Part Score + AI Scan + Fixes           |
                        |              v                                  |
                   /edit-resume --> Refined Package                       |
```

### SWE / DevOps Pipeline
```
Positions + Projects --> /swe-setup --> Knowledge Base (2 Persona Variants)
                            |            - experience_*_devops.md
                            |            - experience_*_swe.md
                            |            - projects/*.md
                            |            - 2 bundles (DevOps + SWE)
                            v
Job Description --> /make-resume --> Persona Detection --> Tailored Resume (.tex)
  (DevOps or SWE)        |                 |               (1-page, auto-selected
                         |                 |                projects)
                    /make-cl --> Cover Letter (.tex)
                         |              v
                    /critique --> 8-Part Score + AI Scan
                         |              v
                    /edit-resume --> Refined Package
```

---

### Skills Reference

| Skill | Purpose | Input | Output | Track |
|-------|---------|-------|--------|-------|
| `/swe-setup` | Build SWE KB from work history | Interactive Q&A | `resume_builder/{experience,bundles,projects,support}/` | SWE |
| `/setup-extract` | Extract data from papers | Paper PDF/tex | `knowledge_base/extractions/*.md` | Researcher |
| `/setup-build-kb` | Build researcher KB | All extractions | `resume_builder/{experience,bundles,support}/` | Researcher |
| `/make-resume` | Generate tailored resume | JD path | `output/<Folder>/e2e_*.tex` + session | Both |
| `/make-cl` | Generate matching cover letter | Session file | `output/<Folder>/*_cover_letter.tex` | Both |
| `/edit-resume` | Edit resume/CV/CL from feedback | Session + feedback | Updated `.tex` files | Both |
| `/critique` | Independent quality review | Session file | `output/<Folder>/critique_*.md` | Both |

---

## Documentation

For architecture details, customization tables, the full critique system breakdown, key design decisions, and FAQ, see **[DOCS.md](DOCS.md)**.

---

## Contributing

Issues and PRs welcome. When contributing:
- Example files use the fictional Dr. Jordan Chen — keep examples in that persona
- Reference docs should stay domain-agnostic
- Test skill changes against the example data before submitting

---

## License

MIT — see [LICENSE](LICENSE).
