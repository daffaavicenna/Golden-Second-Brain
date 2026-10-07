# 📥 Inbox Directory

Drop your raw source documents here for processing by AI agents.

### Supported Formats:
- Markdown (`.md`)
- Plain text (`.txt`)
- PDF documents (`.pdf`)
- Web clips / articles (e.g. from Obsidian Web Clipper or Defuddle)
- Code files or data snippets

### How it works:
1. Put any file you want to ingest into this folder.
2. Tell your AI Agent: *"Tolong ingest file di inbox"* or *"Ingest inbox"*.
3. The AI Agent will:
   - Read and extract key concepts, arguments, and data.
   - Create or update relevant wiki pages in `wiki/`.
   - Update `index.md` and append a timestamped entry to `log.md`.
   - **Move the raw file automatically to `archive/YYYY-MM/`** so it is never reprocessed.
