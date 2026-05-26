# CLAUDE.md

## Repository Overview

`stonecccc/refs` is a minimal image-reference repository. Its primary purpose is to store and version-control image files (JPEG) used in AI image-generation continuation workflows. There is no application code, build system, or test suite.

## Repository Structure

```
refs/
├── README.md      # Single-line title only
└── CLAUDE.md      # This file
```

### Historical assets (removed from current working tree)

Three image files were committed and later emptied out (deleted content, file retained as zero-byte placeholder) in separate "remove image from public hosting" commits:

| File | Original size | Status |
|---|---|---|
| `wanwan.jpg` | ~61 KB | Removed (zero-byte) |
| `wanwan_last_frame.jpg` | ~51 KB | Removed (zero-byte) |
| `wanwan_cont_1779189837.jpg` | ~64 KB | Removed (zero-byte) |

The numeric suffix on `wanwan_cont_1779189837.jpg` is a continuation ID used to link a generated frame back to its source session.

## Naming Conventions

- **Base image**: `<subject>.jpg` — the original reference image (e.g. `wanwan.jpg`)
- **Last frame**: `<subject>_last_frame.jpg` — the final frame extracted before a continuation
- **Continuation frame**: `<subject>_cont_<session_id>.jpg` — the first frame of a continuation run, where `<session_id>` is a numeric ID

## Git Workflow

- Default branch: `main`
- AI-assistant feature branches follow the pattern: `claude/<descriptor>-<random_suffix>` (e.g. `claude/claude-md-docs-TwnMl`)
- Commits are small and focused — one file or one logical action per commit
- Commit message style: lowercase imperative, no period (e.g. `add last frame for continuation test`, `remove image from public hosting`)
- Images that should not remain publicly accessible are emptied in place (zero-byte commits) rather than being fully removed from history, preserving the commit graph

## Development Guidelines for AI Assistants

1. **No build/test commands** — there is no `package.json`, `Makefile`, or test runner. Do not invent or run build steps.
2. **No code changes needed** — this repo holds binary assets, not source code. Avoid creating source files unless the user explicitly requests new functionality.
3. **Branch discipline** — always develop on the designated `claude/*` branch; never push directly to `main` without explicit user instruction.
4. **Commit granularity** — mirror the existing style: one file per commit, short lowercase imperative messages.
5. **Privacy** — image files may contain personal or sensitive content. Do not upload, share, or transmit image content to external services.
6. **README** — the `README.md` intentionally contains only a title (`# refs`). Do not expand it unless asked.
