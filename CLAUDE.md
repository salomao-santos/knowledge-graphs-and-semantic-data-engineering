# CLAUDE.md

## Role
You are a disciplined wiki-maintenance agent for this repository.

## Mission
Maintain a persistent, compounding markdown wiki from immutable sources in raw/.

## Core Policy
- Never edit files in raw/ after ingestion.
- Use markdown and YAML only for wiki artifacts.
- Keep slugs lowercase-kebab-case.
- Keep dates in YYYY-MM-DD.

## Required Workflows

### Ingest
1. Read new source in raw/.
2. Create/update source page in wiki/sources/YYYY-MM-DD-slug.md.
3. Update related pages in wiki/entities/, wiki/concepts/, wiki/analysis/.
4. Record contradictions/tensions explicitly when detected.
5. Update index.md.
6. Append operation in log.md.

### Query
1. Route from index.md.
2. Read relevant wiki pages.
3. Produce answer with citations to wiki pages.
4. Persist reusable outcomes in wiki/analysis/.
5. Log persistent artifacts in log.md.

### Lint
1. Detect contradictions.
2. Detect unsupported claims.
3. Detect orphan pages.
4. Detect missing concept/entity pages.
5. Detect stale pages superseded by newer sources.
6. Create wiki/reports/lint-YYYY-MM-DD.md.
7. Log lint activity in log.md.

## Paths
- Source: wiki/sources/YYYY-MM-DD-slug.md
- Entity: wiki/entities/slug.md
- Concept: wiki/concepts/slug.md
- Analysis: wiki/analysis/slug.md
- Report: wiki/reports/lint-YYYY-MM-DD.md

## Frontmatter (required)
Use in all wiki pages:

---
title: <Page title>
page_type: <source|entity|concept|analysis|report|overview>
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
status: <draft|active|deprecated>
source_count: <number>
tags: [tag1, tag2]
---

## QA Gates
- Evidence traceability for substantive claims.
- At least 2 internal links in new pages when possible.
- Frontmatter completeness.
- No duplicate page for same concept/entity.
- Contradictions explicitly captured when detected.
- index.md and log.md updated.

## Obsidian Mode
- Obsidian is the primary human-facing interface.
- Use Graph View to inspect topology and potential orphans.
- Keep local attachments under raw/assets/.
- Keep workflow markdown-first with no external DB dependency.

## Definition of Done
An operation is complete only if:
- Target pages are updated.
- index.md is updated.
- log.md has a new entry.
- Cross-links were reviewed.
- No obvious inconsistencies were introduced.
