# CLAUDE.md

This repository follows the universal multi-agent schema defined in [AGENTS.md](AGENTS.md).

Please strictly adhere to all guidelines, protocols, and workflows documented in `AGENTS.md`:
- **Language Protocol**: Internal wiki content (`wiki/**`, `index.md`, `log.md`) is written in English. All user conversations and explanations are in Bahasa Indonesia.
- **Onboarding Protocol**: Always check `wiki/entities/User Profile.md` first. If uninitialized, guide the user through onboarding before processing files.
- **Ingest Pipeline**: Ingest raw files from `inbox/`, compile into `wiki/`, update `index.md` & `log.md`, move raw files to `archive/YYYY-MM/`, and commit with git.
- **Skills Hub**: All skills and runbooks are centralized in `.agents/skills/`. Read and execute skills directly from `.agents/skills/`.
- **Conventions**: Use Title Case file names and Obsidian Flavored Markdown with `[[wikilinks]]`.

See [AGENTS.md](AGENTS.md) for full operational specifications.
