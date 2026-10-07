# 📦 Archive Directory

This directory stores raw source documents that have been ingested into the wiki.

### Principles:
1. **Immutable Source of Truth**: Files here are preserved in their original state. AI agents read them for citations or verification, but never edit or delete them.
2. **Organized by Ingestion Date**: Files are moved here into subfolders formatted as `archive/YYYY-MM/` (e.g. `archive/2026-10/`).
3. **No Redundant Processing**: Any file residing in `archive/` is considered already integrated into `wiki/`.
