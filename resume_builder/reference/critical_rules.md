# Critical Rules — Compact Re-Read

> Quick reference for Phase 2 generation. Full rules in `resume_reference.md`.

## Character Limits

**Resume (10pt, textwidth=7.5in):**

| Target Lines | Rendered Char Range | HARD MAX | Orphan Threshold |
|-------|---------------|---------|------------------|
| 1 line | 105-111 chars | 117 | -- |
| 2 lines | 189-205 chars | 218 | Last line >= 78 chars |

### Variant Naming

| Variant | Document | Lines | Target Range | HARD MAX | Orphan | Word Target |
|---------|----------|-------|-------------|----------|--------|-------------|
| Resume-1L | 1-page resume | 1 | 105-111 | 117 | -- | ~13 words |
| Resume-2L | 1-page resume | 2 | 189-205 | 218 | >= 78 | ~23-25 words |

## Bold Width Penalty

Resume (10pt): Effective limit = 119 - (0.5 x bold_char_count)

## Orphan Rule

Multi-line bullet last rendered line must fill >= 70% of line width.
Resume 2L: last line >= 78 chars.

## FIXED Sections — NEVER Modify

All FIXED sections (education, honors/awards, header block) are set in the template.
NEVER change: \vspace values, \geometry settings, .cls formatting, header layout.
Only modify VARIABLE sections: Summary, Technical Skills, Experience bullets/headers, Projects.

## LaTeX Notation Quick-Ref

| Item | Correct LaTeX | Wrong | Rendered |
|------|--------------|-------|----------|
| Superscript labels | `X$^2$Y` | `X2Y` | X²Y |
| Approximately | `$\sim$64` | `~64` (LaTeX non-breaking space!) | ~64 |
| Hyphens | `--` (en-dash) | `-` (hyphen) | – vs - |

CRITICAL: ~ in LaTeX = non-breaking space. Use $\sim$ for "approximately."

## Accuracy Tracking

Before generation, verify all metrics against experience files:
- Latency/performance numbers verified? ✓
- User count or scale accurate? ✓
- Ownership level correct (solo vs team)? ✓

## Budget Reminder

Resume: ~8-10 experience bullets + 2-6 project bullets (1-page total).
Resume bullets: ALL 2L.
Project bullets: 1-2 per project, 2L format.
Skills: 4-3-2-2 config (11 lines).
