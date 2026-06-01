# Prompt: LLM Wiki Repository Setup (EN)

Use this prompt with Claude Code, GitHub Copilot Agent, or Antigravity.

## Instructions to the Agent

You are an implementation agent running at the repository root. Build a complete LLM Wiki setup using markdown and YAML only (no generated code files, no scripts as deliverables).

Primary objective:
- Create and configure a persistent wiki workflow where raw sources are immutable and the wiki is incrementally maintained by the LLM.

Required compatibility targets:
- Claude Code (CLAUDE.md)
- GitHub Copilot (copilot-instructions.md)
- Antigravity (copilot-instructions.md)

## Constraints

- Use only markdown and YAML in created artifacts.
- Assume Obsidian is the default frontend and make this explicit in docs.
- Do not create a first-run ingest task with sample content.
- Keep naming ASCII-only and kebab-case for slugs.
- Treat raw/ as immutable after ingest.

## Deliverables

Create or update all items below:

1. Root instruction files
- CLAUDE.md
- copilot-instructions.md
- AGENTS.md

2. Repository structure
- raw/
- raw/assets/
- wiki/
- wiki/sources/
- wiki/entities/
- wiki/concepts/
- wiki/analysis/
- wiki/reports/
- schema/templates/

3. Operational files
- index.md
- log.md
- wiki/Home.md

4. Templates (markdown with YAML frontmatter)
- schema/templates/source-summary.md
- schema/templates/entity-page.md
- schema/templates/concept-page.md
- schema/templates/analysis-page.md
- schema/templates/lint-report.md

## Required policy content

Your created instruction files must define all of the following:

1. Ingest workflow
- Read new source in raw/
- Summarize source to wiki/sources/YYYY-MM-DD-slug.md
- Update affected entity/concept/analysis pages
- Register contradictions/tensions where applicable
- Update index.md
- Append entry to log.md

2. Query workflow
- Route via index.md first
- Read relevant wiki pages
- Produce synthesized answer with citations to wiki pages
- Persist reusable outputs into wiki/analysis/
- Log persistent artifacts in log.md

3. Lint workflow
- Detect contradictions
- Detect unsupported claims
- Detect orphan pages
- Detect missing concept/entity pages
- Detect stale pages superseded by newer sources
- Produce report in wiki/reports/lint-YYYY-MM-DD.md
- Log lint activity

4. Naming and structure rules
- Date format: YYYY-MM-DD
- Slug format: lowercase-kebab-case
- Source page path: wiki/sources/YYYY-MM-DD-slug.md
- Entity page path: wiki/entities/slug.md
- Concept page path: wiki/concepts/slug.md
- Analysis page path: wiki/analysis/slug.md
- Report path: wiki/reports/lint-YYYY-MM-DD.md

5. Definition of Done (DoD)
An operation is complete only if:
- Target pages are updated
- index.md is updated
- log.md has an appended entry
- cross-links were reviewed
- no obvious inconsistencies were introduced

6. QA gates
Before finalizing any operation, run these checks:
- Gate 1: Evidence traceability present for substantive claims
- Gate 2: At least 2 internal links in new pages when possible
- Gate 3: Frontmatter completeness
- Gate 4: No duplicate page for same concept/entity
- Gate 5: Contradictions explicitly recorded when detected
- Gate 6: index.md and log.md both updated

## Frontmatter schema (required)

Use this frontmatter in all wiki pages (adapt values per page):

```yaml
---
title: <Page title>
page_type: <source|entity|concept|analysis|report|overview>
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
status: <draft|active|deprecated>
source_count: <number>
tags: [tag1, tag2]
---
```

## Obsidian-specific requirements

Document the following in wiki/Home.md or AGENTS.md:
- Obsidian as primary browsing/editing interface for human users
- Recommended use of graph view for topology checks
- Recommendation to store clipped article attachments in raw/assets/
- Markdown-first workflow with no dependency on external DB

## Output format

At the end, provide:
1. A concise tree of created/updated files
2. A short summary of decisions
3. Any assumptions made

Implement now.