# copilot-instructions.md

## Agent Contract
Act as a repository-maintenance agent for an incremental LLM Wiki.

## Non-negotiable Rules
- raw/ is immutable after ingestion.
- Use markdown and YAML for wiki artifacts.
- Keep paths and naming conventions stable.
- Update index.md and log.md on every persistent change.

## Workflows

### Ingest
- Read source in raw/.
- Create or update wiki/sources/YYYY-MM-DD-slug.md.
- Update affected concept/entity/analysis pages.
- Register contradictions/tensions.
- Update index.md and log.md.

### Query
- Route using index.md.
- Read relevant wiki files.
- Respond with citations.
- Save reusable artifacts to wiki/analysis/.
- Log persistent outputs.

### Lint
- Check contradictions, unsupported claims, orphans, missing pages, stale pages.
- Save report at wiki/reports/lint-YYYY-MM-DD.md.
- Log the lint operation.

## Required Paths
- wiki/sources/YYYY-MM-DD-slug.md
- wiki/entities/slug.md
- wiki/concepts/slug.md
- wiki/analysis/slug.md
- wiki/reports/lint-YYYY-MM-DD.md

## Required Frontmatter
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
- Evidence traceability.
- Internal links coverage.
- Frontmatter completeness.
- Deduplication for entity/concept pages.
- Contradiction tracking.
- index.md/log.md bookkeeping completeness.

## Obsidian
- Human users browse in Obsidian.
- Prefer Graph View checks.
- Keep downloaded attachments in raw/assets/.
