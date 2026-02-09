# Resume Optimization Deep Research Project

## Purpose

Evidence-based research to determine the optimal resume structure, format, tone, word choice, and strategy for a senior management consultant (10 years, financial services) targeting AI governance/enablement roles at VP/Senior Manager level.

Research output becomes skill files and documentation used by a claude.ai project to build the actual resume.

## Project Structure

```
agent_docs/          ← Dimension specs (read before researching)
  dimensions.md      ← Master list of all 10 dimensions with priority order
  D01_structure.md   ← through D10_industry.md (one per dimension)
  candidate.md       ← Full candidate profile and context
  seed_data.md       ← Pre-gathered findings to verify
research/            ← Research outputs (one file per dimension)
  D07_tone.md        ← through D10_industry.md
output/              ← Final deliverables
  SKILL.md           ← Resume blueprint as a skill file for claude.ai
  verb_reference.md  ← Curated verb sheet
  keyword_matrix.md  ← Master keyword list
reference/           ← Input materials
  current_resume.md  ← Current resume as plain text
tracking.md          ← Running status table (update after each dimension)
```

## Rules

1. **ALWAYS use web search.** Every dimension requires live web research. Do not answer from training knowledge. Only cite sources actually retrieved and verified in this session. Never fabricate URLs or statistics.

2. **Read before researching.** Before starting any dimension, read `agent_docs/candidate.md` and the relevant `agent_docs/D##_*.md` file for research questions and source targets.

3. **Source hierarchy.** Weight in this order:
   - Tier 1: Peer-reviewed research, published studies with methodology
   - Tier 2: Top-tier university career services (Harvard, Columbia, Yale, Wharton)
   - Tier 3: Recruiter surveys with disclosed methodology (Jobscan, TheLadders)
   - Tier 4: Expert practitioners in authoritative publications (HBR, HR Dive)
   - Tier 5: Consulting-specific career guides (Leland, IGotAnOffer)
   - REJECT: Unsourced blogs, resume builder marketing, AI content farms

4. **Verify seed data.** Read `agent_docs/seed_data.md` — it contains pre-gathered findings. Verify each claim via web search before building on it. Flag anything unverifiable.

5. **Specificity over generality.** Every recommendation must be specific to this candidate's profile. Generic resume advice is worthless. Filter through: 10-year consultant, financial services, AI governance target, non-traditional AI background, SUNY Albany, VP/Senior Manager level.

6. **Update tracking.** After completing any dimension, update `tracking.md` with status, confidence level, and one-sentence key recommendation.

7. **Language rules for any example text generated:**
   - Never use "vibe coding" — use "self-directed prototyping"
   - Never frame prototyping as engineering credentials — always governance/risk lens
   - Ban: "passionate about," "excited about," "leverage synergies," "results-driven," "detail-oriented," "team player," "responsible for," "duties included," "utilized," "various," "several," "helped," "assisted"

## Research Workflow

For each dimension:
1. Read the dimension spec from `agent_docs/`
2. Read `agent_docs/candidate.md` for profile context
3. Run 5-15 web searches targeting highest-authority sources
4. Fetch full articles when snippets are insufficient
5. Identify conflicts and gaps, run targeted follow-up searches
6. Filter all findings through candidate's specific profile
7. Write output to `research/D##_name.md` in the required format
8. Update `tracking.md`

## Output Format for Research Files

Each `research/D##_name.md` must follow this structure:

```markdown
# Dimension [#]: [Name]

## Evidence Summary
[Findings grouped by sub-question, with inline citations]

## Cross-References
[Dependencies on other dimensions]

## Recommendation for Matthew
[Specific, actionable guidance for resume drafting]

## Example Application
[Before/after or concrete example using his actual resume content]

## Sources (Verified)
1. [Title, Author/Institution, Date, URL]

## Confidence Assessment
- Overall: High / Medium / Low
- Rationale: [Source quality, consensus, applicability]

## Open Questions
[Areas needing more research or candidate input]
```

## Final Deliverable

After all 10 dimensions are researched, synthesize into `output/SKILL.md` — a skill file that can be uploaded to claude.ai. The SKILL.md must be specific enough that Claude can draft the resume directly from it without referencing individual dimension outputs. It must resolve all cross-dimensional tensions.

## Running This Project

Use Opus 4.6 with extended thinking. Start Claude Code with: `claude --model claude-opus-4-6`

Research one dimension at a time. Use the custom commands:
- `/research D7` — research a specific dimension
- `/status` — show current tracking table
- `/synthesize` — produce the final SKILL.md after all dimensions are complete
