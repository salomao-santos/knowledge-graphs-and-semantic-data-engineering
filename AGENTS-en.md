# AGENTS-en.md

Operational schema to maintain an incremental LLM Wiki in this repository.

## 1. Objective
Maintain a persistent, interlinked, cumulative markdown wiki using immutable sources in raw/ and derived artifacts in wiki/.

## 2. Repository Structure
- raw/: original immutable sources.
- raw/assets/: local attachments (images, media).
- wiki/: pages generated and maintained by the agent.
- schema/templates/: templates used to standardize pages.
- index.md: content-oriented catalog.
- log.md: append-only chronological history.

## 3. Global Rules
1. Do not edit files in raw/ after ingestion.
2. Every ingest must update index.md and log.md.
3. Every new wiki page should include at least 2 internal links when possible.
4. If contradictions are detected, record them in a "Contradictions/Tensions" section.
5. Avoid duplication: update existing pages before creating new ones.
6. Preserve traceability: substantive claims must reference source pages and/or raw files.
7. Keep naming ASCII and lowercase-kebab-case.

## 4. Path Conventions
- Source pages: wiki/sources/YYYY-MM-DD-slug.md
- Entity pages: wiki/entities/slug.md
- Concept pages: wiki/concepts/slug.md
- Analysis pages: wiki/analysis/slug.md
- Lint reports: wiki/reports/lint-YYYY-MM-DD.md

## 5. Required Frontmatter
All wiki pages must include:
- title
- page_type (source|entity|concept|analysis|report|overview)
- created
- updated
- status (draft|active|deprecated)
- source_count
- tags

## 6. Workflow: Ingest
When a new source arrives in raw/:
1. Read and extract key claims/evidence.
2. Create or update a source page in wiki/sources/.
3. Update related entity/concept/analysis pages.
4. Register contradictions and confidence changes if any.
5. Update index.md with link and one-liner.
6. Append a log.md entry.

## 7. Workflow: Query
When answering user questions:
1. Route from index.md.
2. Read relevant wiki pages.
3. Provide synthesized answers with citations to wiki pages.
4. Persist reusable outputs in wiki/analysis/.
5. Append log entry when a persistent artifact is created.

## 8. Workflow: Lint
Periodically verify:
- Contradictions across pages.
- Unsupported substantive claims.
- Orphan pages when detectable.
- Mentioned concepts/entities with missing dedicated pages.
- Stale pages superseded by newer sources.

Generate report in wiki/reports/lint-YYYY-MM-DD.md and append to log.md.

## 9. QA Gates (Mandatory)
Before completing any operation:
1. Evidence Gate: claims have traceable evidence.
2. Linking Gate: new pages contain internal links when possible.
3. Frontmatter Gate: required metadata fields are present.
4. Dedup Gate: no duplicate pages for same concept/entity.
5. Contradiction Gate: tensions explicitly captured.
6. Bookkeeping Gate: index.md and log.md updated.

## 10. Obsidian Mode
- Obsidian is the default human-facing interface.
- Use Graph View to monitor page topology.
- Keep article/media attachments in raw/assets/.
- Keep workflow markdown-first, no external database required.

## 11. Definition of Done (DoD)
An operation is complete only when:
- Target files are updated.
- index.md is updated.
- log.md has a new entry.
- Internal links are reviewed.
- No obvious inconsistency was introduced.
