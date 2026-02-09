Synthesize all completed research dimensions into the final SKILL.md file.

## Prerequisites

All 10 dimensions must have status "Complete" in `tracking.md`. If any are incomplete, list them and stop.

## Instructions

1. Read `tracking.md` to confirm all dimensions are complete.
2. Read ALL research files from `research/` (D01 through D10).
3. Read `agent_docs/candidate.md` for profile context.
4. Read `reference/current_resume.md` for the current state.
5. Read any files already in `output/` (verb_reference.md, keyword_matrix.md).

## Synthesis Task

Create `output/SKILL.md` — a self-contained skill file that can be uploaded to a claude.ai project. When Claude reads this skill file before building a resume, it must have everything it needs to produce a resume that reflects all 10 dimensions of research.

The SKILL.md must include:

### 1. Metadata Block
```
---
name: resume-builder
description: Evidence-based resume construction guide for Matthew Pensa targeting AI governance/enablement roles in financial services. Use this skill whenever creating, editing, or tailoring Matthew's resume.
---
```

### 2. Candidate Profile Summary
Condensed from candidate.md — enough context that Claude understands who it's writing for.

### 3. Resume Architecture
- Exact section order with rationale
- Page allocation (what goes on page 1 vs. page 2)
- Section-level formatting specs (fonts, sizes, margins, spacing)

### 4. Professional Summary Template
- Structure and length
- First-15-words formula
- Fill-in guidance with constraints

### 5. Bullet Construction Rules
- Formula with annotated examples
- Tone markers (senior vs. junior)
- Governance-work quantification guidance
- Do-this / not-this pairs

### 6. Verb Reference
- Categorized by work type
- Banned verbs list
- Repetition limits

### 7. Keyword Strategy
- Master keyword list by category
- Placement rules (summary, skills section, within bullets)
- ATS optimization rules

### 8. Career Evolution Framing
- How to frame: risk consulting → AI governance
- AI fluency section placement and content
- Engagement-to-AI-governance mapping (which bullets connect to which AI governance capability)

### 9. Early Career Handling
- Citizens Bank / TD Bank treatment
- Education section placement and content

### 10. Cross-Dimensional Tensions — Resolved
Where research dimensions produced conflicting guidance, document the resolution and rationale. Examples:
- Keyword density vs. natural tone
- AI prominence vs. engineering-role routing risk
- Bullet length vs. scanability
- MBB rigor vs. senior professional format

### 11. Quality Checklist
A final checklist Claude can run against any draft to verify compliance with all research findings.

## Output

Write the complete SKILL.md to `output/SKILL.md`.
Update `tracking.md` to mark "Blueprint Synthesis" as complete.
Display a summary of key decisions made during synthesis.
