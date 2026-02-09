# Resume Optimization Deep Research — Setup Guide

## What This Is

A Claude Code project that researches 10 dimensions of resume optimization, then synthesizes findings into a `SKILL.md` file you can upload to your claude.ai career strategist project. That skill file becomes the blueprint Claude follows every time it builds or tailors your resume.

## Setup

### 1. Prerequisites

- Claude Code installed (`npm install -g @anthropic-ai/claude-code`)
- Max plan with Opus 4.6 extended thinking enabled

### 2. Clone / Copy This Project

Copy the entire `RESUME-FORMAT-DESIGNER/` folder to wherever you keep projects.

### 3. Start Claude Code with Opus

```bash
cd RESUME-FORMAT-DESIGNER
claude --model claude-opus-4-6
```

Opus 4.6 with extended thinking is the ideal configuration. The CLAUDE.md is designed for Opus-level reasoning depth — extended thinking lets it work through source conflicts and candidate-specific filtering before writing output.

### 4. Verify Setup

```bash
find . -name "*.md" -not -path "./.git/*" | wc -l
# Should output: 21
```

## Usage

### Research a Dimension

```
/research D7
```

Or omit the argument to research the next dimension in priority order:

```
/research
```

Each dimension takes 5-15 minutes depending on search depth. Claude will:
1. Read the dimension spec and candidate profile
2. Run web searches
3. Write findings to `research/D##_name.md`
4. Update `tracking.md`

### Check Progress

```
/status
```

### Review a Completed Dimension

```
/review D7
```

Checks for gaps, unverified claims, or generic recommendations.

### Synthesize the Final Skill File

After all 10 dimensions are complete:

```
/synthesize
```

This reads all research files and produces `output/SKILL.md`.

## Research Order

| Session | Dimension | Why This Order |
|---------|-----------|---------------|
| 1 | D7: Tone & Word Choice | Foundational — governs all writing |
| 2 | D3: Bullet Construction | Core content unit |
| 3 | D2: Professional Summary | First 15 words frame everything |
| 4 | D1: Structure & Sections | Architectural decisions |
| 5 | D8: Career Evolution | Strategic positioning |
| 6 | D4: Action Verbs | Sentence-level optimization |
| 7 | D5: Keywords & ATS | Technical optimization |
| 8 | D6: Formatting | Implementation details |
| 9 | D9: Length & Pages | Space allocation |
| 10 | D10: Industry & Competitors | Real-world validation |
| Final | Synthesis | Integrate → SKILL.md |

## After Research Is Complete

1. Copy `output/SKILL.md` from this project
2. In your claude.ai career strategist project, upload it as a user skill (or add to project knowledge)
3. When you ask Claude to build or tailor your resume, it will read the skill file first and follow the research-backed blueprint

## Tips

- **Don't rush.** One dimension per session gives best results. The compounding effect of later dimensions building on earlier findings is the whole point.
- **Use /review** after any dimension you're not confident about. Better to catch gaps before synthesis.
- **Context management:** If a session gets long, Claude Code will auto-compact. The research files on disk persist regardless.
- **Editing findings:** You can manually edit any `research/D##.md` file if you disagree with a recommendation. Claude will read your edits when it gets to synthesis.
