# LLM Wiki

A pattern for building personal knowledge bases using LLMs.

This is an idea file, designed to be copy-pasted into your own LLM Agent (e.g., OpenAI Codex, Claude Code, OpenCode / Pi, etc.). Its goal is to communicate the high-level idea; your agent can then build out specifics in collaboration with you.

## The core idea

Most people's experience with LLMs and documents looks like RAG: you upload a collection of files, the LLM retrieves relevant chunks at query time, and generates an answer. This works, but the LLM is rediscovering knowledge from scratch on every question. There is no accumulation. Ask a subtle question that requires synthesizing five documents, and the LLM has to find and piece together relevant fragments every time. Nothing gets built up. NotebookLM, ChatGPT file uploads, and most RAG systems work this way.

The idea here is different. Instead of retrieving from raw documents at query time, the LLM incrementally builds and maintains a persistent wiki: a structured, interlinked collection of markdown files that sits between you and the raw sources. When you add a new source, the LLM does not just index it for later retrieval. It reads it, extracts key information, and integrates it into the existing wiki by updating entity pages, revising topic summaries, noting contradictions with old claims, and strengthening or challenging the evolving synthesis. The knowledge is compiled once and then kept current, not re-derived for every query.

This is the key difference: the wiki is a persistent, compounding artifact. Cross-references are already there. Contradictions are already flagged. The synthesis already reflects everything you have read. The wiki keeps getting richer with every source you add and every question you ask.

You rarely write the wiki yourself; the LLM writes and maintains it. You stay in charge of sourcing, exploration, and asking good questions. The LLM handles summarizing, cross-referencing, filing, and bookkeeping that make a knowledge base useful over time. In practice, you can keep an LLM agent open on one side and Obsidian on the other. The LLM edits files based on your conversation; you browse results in real time through links, graph view, and updated pages. Obsidian is the IDE, the LLM is the programmer, and the wiki is the codebase.

This applies to many contexts:

- Personal: goals, health, psychology, self-improvement from journals, articles, and podcast notes.
- Research: deep topic exploration over weeks or months with an evolving thesis.
- Reading a book: chapter-by-chapter filing with character/theme/plot pages and cross-links.
- Business/team: an internal wiki maintained from Slack threads, meetings, documents, and calls.
- Competitive analysis, due diligence, trip planning, course notes, hobby deep-dives.

## Architecture

There are three layers:

**Raw sources**: your curated source documents (articles, papers, images, data files). These are immutable; the LLM reads from them but never modifies them.

**The wiki**: a directory of LLM-generated markdown pages (summaries, entities, concepts, comparisons, synthesis). The LLM owns this layer: creating pages, updating them with new sources, maintaining cross-references, and keeping consistency.

**The schema**: a control document (e.g., `CLAUDE.md` for Claude Code or `AGENTS.md` for Codex) that defines wiki structure, conventions, and workflows for ingest/query/maintenance. This configuration makes the LLM a disciplined wiki maintainer rather than a generic chatbot.

## Operations

**Ingest**

You add a source and ask the LLM to process it. Typical flow:

1. Read source.
2. Discuss key takeaways with you.
3. Write/update source summary page.
4. Update index.
5. Update relevant entity/concept/topic pages.
6. Append log entry.

A single source may touch 10-15 wiki pages. You can ingest one-by-one with close supervision or batch many items with less supervision.

**Query**

You ask questions against the wiki. The LLM finds relevant pages, reads them, and synthesizes an answer with citations. Outputs can be markdown pages, comparison tables, slide decks (Marp), charts (matplotlib), or canvases. Valuable answers should be filed back into the wiki as new pages so explorations compound over time.

**Lint**

Periodically run a wiki health check:

- Contradictions between pages.
- Stale claims superseded by newer sources.
- Orphan pages with no inbound links.
- Important concepts mentioned but missing their own page.
- Missing cross-references.
- Data gaps that could be filled by web search.

## Indexing and logging

Two special files help at scale:

**index.md** (content-oriented): catalog of wiki pages, each with link + one-line summary, optionally metadata (date, source count), grouped by category. LLM updates this every ingest and uses it first during query routing.

**log.md** (chronological): append-only history of ingests, queries, and lint passes.

Use consistent prefixes in headings, for example:

`## [2026-04-02] ingest | Article Title`

This makes log parsing easy with tools like:

`grep "^## \[" log.md | tail -5`

## Optional: CLI tools

As the wiki grows, small helper tools improve operation. A search tool is the obvious first step. At small scale, `index.md` may be enough; at larger scale, add stronger search.

- `qmd` is a local markdown search engine with BM25/vector hybrid search and LLM reranking, on-device.
- It offers both CLI and MCP interfaces.
- You can also build a simpler custom script first.

## Tips and tricks

- Obsidian Web Clipper quickly converts web articles into markdown sources.
- Download images locally for durability and direct LLM inspection.
- Obsidian graph view reveals structure, hubs, and orphan pages.
- Marp enables markdown-native slide decks.
- Dataview can query frontmatter-driven metadata.
- The wiki is just a git repo, so you get history, branching, and collaboration.

## Why this works

The hard part of knowledge management is not reading or thinking. It is bookkeeping: keeping summaries current, maintaining cross-references, and propagating new evidence across many pages. Humans abandon wikis because maintenance cost grows faster than value. LLMs can do repetitive maintenance consistently and cheaply, including multi-file updates in one pass.

The human role: curate sources, direct analysis, ask good questions, and interpret meaning.

The LLM role: maintain structure, consistency, and compounding knowledge artifacts.

This idea is related to Vannevar Bush's Memex (1945): a personal, curated knowledge store built on associative trails. LLMs can now provide the missing maintenance layer.

## Note

This document is intentionally abstract. It explains a pattern, not a single implementation. Directory layout, schema conventions, page templates, and tools should be adapted to your domain and workflow. Everything here is modular: use what helps, ignore what does not. The best way to apply this is to share it with your LLM agent and co-design the implementation iteratively.