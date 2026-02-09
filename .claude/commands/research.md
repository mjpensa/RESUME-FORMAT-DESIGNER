Research a specific dimension of the resume optimization project.

## Instructions

1. Read `agent_docs/dimensions.md` to confirm the dimension number and its dependencies.
2. Read `agent_docs/candidate.md` for the full candidate profile.
3. Read the dimension spec file from `agent_docs/` (e.g., `agent_docs/D07_tone.md` for D7).
4. Read `agent_docs/seed_data.md` and note any claims relevant to this dimension — these must be verified via web search.
5. If this dimension depends on prior dimensions (check the "Depends On" column), read the completed research files from `research/` to build on those findings.
6. Execute the research workflow:
   - Run 5-15 web searches targeting highest-authority sources per the source hierarchy in CLAUDE.md
   - Fetch full articles when search snippets are insufficient
   - Identify conflicts between sources and run targeted follow-up searches
   - Filter ALL findings through the candidate's specific profile
7. Write the output to `research/D##_name.md` using the exact output format specified in CLAUDE.md.
8. If the dimension spec calls for a deliverable in `output/` (e.g., verb_reference.md, keyword_matrix.md), create that file too.
9. Update `tracking.md` with: status → Complete, confidence level, and a one-sentence key recommendation.
10. After updating tracking, display the updated tracking table.

## Arguments

$ARGUMENTS should be a dimension number (1-10), e.g.: `/research D7` or `/research 7`

If no argument is provided, read `tracking.md` and research the next dimension in priority order that has status "Not started."
