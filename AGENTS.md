# AGENTS.md — Universal Agent Schema & Operating Protocol

This file governs the behavior of all AI agents (Antigravity, Codex, Claude Code, OpenCode, Cursor, Aider, etc.) operating within the **GOLDEN SECOND BRAIN** repository.

---

## 🏛️ Core Philosophy & Mental Model

> **"Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase."** — Andrej Karpathy

- **Persistent, Compounding Knowledge**: Unlike traditional stateless RAG, this system builds and maintains a living, interlinked knowledge base. Knowledge is synthesized once into persistent wiki pages and kept continuously up to date.
- **The Human's Role**: Curator, thinker, and explorer. Directs investigations, provides raw sources, and asks high-level questions.
- **The Agent's Role**: Knowledge engineer and maintainer. Extracts insights, cross-references concepts, flags contradictions, tracks entities, and maintains directory hygiene.

---

## 🌐 Language Protocol (Strict & Mandatory)

1. **Internal Wiki Content (`wiki/**`, `index.md`, `log.md`)**:
   - **MUST be written 100% in English.**
   - Rationale: English provides maximum tokenizer density (lower cost/higher context capacity) and superior semantic embedding across all LLM architectures.
2. **User Interactions & Chat Responses**:
   - **MUST be conducted in Bahasa Indonesia** (unless explicitly requested otherwise by the user).
   - Explain findings, deliver summaries, and discuss plans in Indonesian while keeping wiki file titles, concepts, and markdown text in English.

---

## 🚀 Boot & Onboarding Protocol

Whenever a new session starts:
1. **Check User Identity**: Read `wiki/entities/User Profile.md`.
2. **Evaluate Onboarding Status**:
   - If the file contains `[PENDING_ONBOARDING]` or placeholder tags:
     - **Do NOT begin ingestion immediately.**
     - Greet the user warmly in **Bahasa Indonesia**.
     - Conduct a brief, friendly onboarding interview asking:
       1. Nama / Nama panggilan mereka.
       2. Peran, profesi, atau fokus utama saat ini.
       3. Minat teknis atau bidang keahlian yang sedang ditekuni.
       4. Proyek aktif yang sedang dikerjakan.
     - Update `wiki/entities/User Profile.md` with their answers, update `index.md`, append an entry in `log.md`, and execute `git commit -m "chore: complete user onboarding"`.
3. **If User Profile is already completed**:
   - Silently ground yourself in the user's background, active projects, and preferences to personalize all subsequent interactions.

---

## 📁 Repository Architecture & Layer Rules

```text
Golden Second Brain/
├── inbox/                  # 📥 STAGING LAYER: Raw incoming sources (immutable until ingested)
├── archive/YYYY-MM/        # 📦 PRESERVATION LAYER: Immutable repository of processed raw sources
│
├── wiki/                   # 🧠 PERSISTENT WIKI LAYER: Fully managed & maintained by AI
│   ├── concepts/           # Core theories, mental models, patterns, frameworks
│   ├── entities/           # Specific people, software, organizations, projects, User Profile
│   ├── summaries/          # Structural extractions and takeaways of source documents
│   └── synthesis/          # Cross-domain analyses, deep comparisons, query answers
│
├── index.md                # 📖 Master content catalog, updated on every ingest
├── log.md                  # 📜 Chronological, parseable audit trail of all vault operations
│
├── .agents/                # 🤖 Agent skills, rules, and extensions
├── AGENTS.md               # ⚙️ Master multi-agent configuration (this file)
├── CLAUDE.md               # ⚙️ Pointer for Claude Code
└── GEMINI.md               # ⚙️ Pointer for Gemini / Antigravity
```

### Layer Boundary Rules:
- **`inbox/`**: The human drops files here. The agent reads from here, then **moves** the file to `archive/YYYY-MM/` upon ingest completion.
- **`archive/`**: Read-only source of truth. Never edit, modify, or delete files here.
- **`wiki/`**: Read/write by AI agent. Human reads in Obsidian. Every concept or entity uses **Title Case** (e.g., `wiki/concepts/Transformer Architecture.md`).

---

## ⚡ Core Operational Workflows

### 1. Ingest Operation (`/ingest` or user requests ingestion)
Execute the following steps methodically:
1. **Scan `inbox/`**: Identify all unprocessed files in `inbox/` (ignore `README.md`).
2. **Read & Analyze**: Parse the full content of the raw document.
3. **Generate Summary**:
   - Create `wiki/summaries/<Document Title>.md`.
   - Include YAML frontmatter: `type: summary`, `source_date`, `tags`, `original_filename`.
   - Provide executive summary, key claims, key quotes, and related concepts.
4. **Update / Create Concept & Entity Pages**:
   - Check existing pages in `wiki/concepts/` and `wiki/entities/`.
   - Create new concept/entity pages if significant topics are introduced.
   - Update existing pages with new evidence, noting nuances or contradictions:
     `> [!note] Ingested from [[<Document Title>]] on YYYY-MM-DD: <new insight>`
   - Interlink everything using Obsidian wikilinks: `[[Concept Name]]`, `[[Entity Name]]`.
5. **Update `index.md`**:
   - Add new entries to the appropriate tables with a 1-line description and date.
6. **Append to `log.md`**:
   - Append: `## [YYYY-MM-DD] ingest | <Document Title>`
   - Include bulleted summary of files created and touched.
7. **Archive Raw Document**:
   - Create destination directory `archive/YYYY-MM/` if it does not exist.
   - Move the raw file from `inbox/<filename>` to `archive/YYYY-MM/<filename>`.
8. **Git Commit**:
   - Execute: `git add . && git commit -m "ingest: <Document Title>"`
9. **Notify User**:
   - Report the completion summary in **Bahasa Indonesia**. Highlight key insights, new pages created, and touched nodes.

---

### 2. Query Operation (`/query` or user questions)
1. **Consult Index**: Read `index.md` to identify relevant concepts, entities, and summaries.
2. **Read Target Pages**: Read the specific wiki notes (avoid brute-force reading all files).
3. **Synthesize Answer**: Respond to the user in **Bahasa Indonesia**, citing wiki pages with `[[Wiki Links]]`.
4. **Compound Synthesis**:
   - If the answer represents a high-value comparison, synthesis, or new insight, file it into `wiki/synthesis/<Topic Title>.md`.
   - Update `index.md` and log the query in `log.md`.

---

### 3. Lint / Health Check Operation (`/lint`)
Periodically inspect vault health:
1. **Orphan Pages**: Detect pages with 0 inbound wikilinks.
2. **Missing Concepts**: Identify concepts mentioned across 3+ summaries that lack their own page in `wiki/concepts/`.
3. **Contradictions**: Flag conflicting claims between ingested sources.
4. **Log Review**: Ensure `index.md` matches actual files on disk.

---

## 📝 Syntax & Formatting Standards

- **Obsidian Flavored Markdown**:
  - Internal links: `[[Note Name]]` or `[[Note Name|Display Text]]`.
  - Embeds: `![[Image.png]]`, `![[Note Name#Section]]`.
  - Callouts: `> [!tip]`, `> [!warning]`, `> [!info]`, `> [!note]`.
- **Frontmatter YAML Template**:
  ```yaml
  ---
  type: concept | entity | summary | synthesis
  created: YYYY-MM-DD
  updated: YYYY-MM-DD
  tags:
    - topic
    - category
  aliases:
    - Alternative Name
  ---
  ```
- **File Names**: Always use **Title Case** with spaces (e.g. `Reinforcement Learning.md`, not `reinforcement-learning.md`).
