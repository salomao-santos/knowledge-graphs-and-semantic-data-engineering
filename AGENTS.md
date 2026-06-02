# AGENTS.md

Operational schema for maintaining an incremental LLM Wiki in this repository.

## 1. Objective
Maintain a persistent, interlinked, cumulative markdown wiki using immutable sources in raw/ and derived artifacts in wiki/.

## 2. Repository Structure
- raw/: immutable source documents.
- raw/assets/: local attachments for clipped content.
- wiki/: generated and maintained knowledge pages.
- schema/templates/: page templates.
- index.md: content-oriented catalog.
- log.md: append-only chronological history.

## 3. Global Rules
1. Never edit files in raw/ after ingestion.
2. Every ingest operation must update index.md and log.md.
3. Every new page should contain at least 2 internal links when possible.
4. When contradictions are found, record them in "Contradictions/Tensions".
5. Avoid duplication: prefer updating existing pages before creating new ones.
6. Keep evidence traceability for substantive claims (source page and/or raw file).
7. Use ASCII naming and lowercase-kebab-case slugs.

## 4. Path Conventions
- Source pages: wiki/sources/YYYY-MM-DD-slug.md
- Entity pages: wiki/entities/slug.md
- Concept pages: wiki/concepts/slug.md
- Analysis pages: wiki/analysis/slug.md
- Lint reports: wiki/reports/lint-YYYY-MM-DD.md

## 5. Required Frontmatter
All pages in wiki/ must include:
- title
- page_type (source|entity|concept|analysis|report|overview)
- created
- updated
- status (draft|active|deprecated)
- source_count
- tags

## 6. Workflow: Ingest
1. Read the source from raw/.
2. Create/update wiki/sources/YYYY-MM-DD-slug.md.
3. Update affected pages in wiki/entities/, wiki/concepts/, wiki/analysis/.
4. Register contradictions/tensions and confidence changes when applicable.
5. Update index.md with link and one-line summary.
6. Append an ingest entry in log.md.

## 7. Workflow: Query
1. Route from index.md.
2. Read relevant wiki pages.
3. Produce a synthesized answer with citations.
4. Persist reusable outputs in wiki/analysis/.
5. Append log.md when persistent artifacts are created.

## 8. Workflow: Lint
Periodically verify:
- Contradictions across pages.
- Unsupported substantive claims.
- Orphan pages (when detectable).
- Missing concept/entity pages.
- Stale pages superseded by newer sources.

Generate report in wiki/reports/lint-YYYY-MM-DD.md and log the operation.

## 9. QA Gates
Before finalizing any operation:
1. Evidence Gate: traceability for substantive claims.
2. Linking Gate: at least 2 internal links in new pages when possible.
3. Frontmatter Gate: required fields present.
4. Dedup Gate: no duplicate page for the same concept/entity.
5. Contradiction Gate: contradictions explicitly recorded when detected.
6. Bookkeeping Gate: both index.md and log.md updated.

## 10. Obsidian Mode
- Obsidian is the primary human-facing interface.
- Use Graph View to inspect topology and identify orphans.
- Keep article attachments in raw/assets/.
- Keep a markdown-first workflow with no external DB dependency.

## 11. Definition of Done (DoD)
An operation is complete only when:
- Target files are updated.
- index.md is updated.
- log.md has a new appended entry.
- Internal links were reviewed.
- No obvious inconsistencies were introduced.
