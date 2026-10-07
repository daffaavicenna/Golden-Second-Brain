# 🧠 GOLDEN SECOND BRAIN

> **An Autonomous, Multi-Agent LLM Wiki & Second Brain Template for Obsidian.**  
> *Inspired by Andrej Karpathy's [LLM Wiki Pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f).*

---

## 💡 The Philosophy

Most AI note-taking systems rely on traditional RAG: you upload documents, retrieve chunks, and the model re-derives insights from scratch every single time. Nothing accumulates.

**Golden Second Brain** changes this paradigm:
- **Obsidian is the IDE.**
- **The LLM Agent is the software engineer.**
- **The Wiki is the persistent, compounding codebase.**

Instead of recalculating insights on every prompt, the LLM continuously reads incoming documents from an `inbox/`, synthesizes them into an interlinked web of Markdown pages (`wiki/`), updates a central catalog (`index.md`), and moves raw sources to `archive/` so they are never re-processed redundantly.

---

## ✨ Key Features

- **Universal Multi-Agent Ready**: Works seamlessly with **Claude Code**, **OpenAI Codex**, **Google Antigravity**, **OpenCode**, **Cursor**, **Aider**, and custom agents via standardized `AGENTS.md`.
- **Zero Redundant Processing**: Raw documents staged in `inbox/` are ingested and automatically moved to `archive/YYYY-MM/`.
- **Bilingual Efficiency Pattern**:
  - **Wiki Storage (100% English)**: Maximum token efficiency (saving 40–60% tokens) and superior semantic density for the AI.
  - **User Interaction (Bahasa Indonesia / User's Native Language)**: AI communicates, explains, and interviews the user in their preferred language.
- **Built-in Obsidian Skills**: Native support for Obsidian Flavored Markdown, wikilinks (`[[Page Name]]`), callouts, tags, Canvas (`.canvas`), and Bases (`.base`).
- **Interactive Onboarding**: New users are guided through an onboarding interview to build `User Profile.md`, giving any AI agent instant context without repetitive introductory prompts.
- **Automatic Version Control**: Automated Git commits track every ingestion step (`git commit -m "ingest: <Title>"`).

---

## 📁 Repository Structure

```text
Golden Second Brain/
├── inbox/                  # 📥 STAGING: Drop raw files here (.md, .pdf, .txt, webclips)
│   └── README.md
├── archive/                # 📦 ARCHIVE: Immutable storage of ingested files
│   └── YYYY-MM/            # (e.g. archive/2026-10/)
│
├── wiki/                   # 🧠 PERSISTENT WIKI (Maintained by LLM)
│   ├── concepts/           # Core theories, mental models, patterns, frameworks
│   ├── entities/           # Specific people, software, organizations, User Profile
│   ├── summaries/          # Structural extractions and takeaways of source documents
│   └── synthesis/          # Cross-domain analyses, deep comparisons, query answers
│
├── index.md                # 📖 Master catalog of all wiki pages
├── log.md                  # 📜 Append-only chronological timeline of vault operations
│
├── .agents/                # 🤖 Agent skills (obsidian-markdown, obsidian-cli, defuddle, etc.)
├── AGENTS.md               # ⚙️ Master multi-agent configuration
├── CLAUDE.md               # ⚙️ Configuration for Claude Code
├── GEMINI.md               # ⚙️ Configuration for Gemini / Antigravity
└── README.md               # 📘 Documentation
```

---

## 🚀 Quick Start Guide

### 1. Clone & Open
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/golden-second-brain.git
   ```
2. Open the cloned folder as a Vault in **Obsidian**.

### 2. Launch Any AI Agent
Launch your preferred AI tool inside the vault root:
- **Claude Code**: `claude`
- **Codex / OpenCode**: `opencode` / `codex`
- **Antigravity / Gemini CLI**: Open workspace in Antigravity

### 3. Complete Onboarding
On your first session, the agent will detect an uninitialized profile in `wiki/entities/User Profile.md` and conduct a quick onboarding interview in Bahasa Indonesia to configure your personal goals, tech stack, and active projects.

### 4. Ingest Your First Document
1. Drop any note, paper, or web clip into `inbox/`.
2. Tell your agent:
   > *"Tolong ingest file yang ada di inbox"*
3. Watch the agent compile the knowledge into `wiki/`, update `index.md`, log the action in `log.md`, and move the raw file into `archive/`.

---

## 🛠️ Operations Reference

| Operation | Command / Prompt | What Happens |
| :--- | :--- | :--- |
| **Ingest** | `ingest inbox` / *"Tolong ingest"* | Reads raw files from `inbox/`, updates `wiki/`, moves raw files to `archive/YYYY-MM/`, updates `index.md` & `log.md`, commits git. |
| **Query** | *"Jelaskan tentang X berdasarkan wiki"* | Searches `index.md`, reads relevant wiki pages, delivers synthesized response. High-value answers are saved to `wiki/synthesis/`. |
| **Lint** | `lint wiki` / *"Cek kesehatan wiki"* | Scans for orphan pages, missing concept notes, claim contradictions, and catalog integrity. |

---

## 📜 License
MIT License. Created with ❤️ for knowledge explorers and PKM enthusiasts.
