# Batocera-Development-RAG

Retrieval-augmented knowledge base for Batocera-related development. Covers multiple projects: [Batocera-CRT-Script](https://github.com/ZFEbHVUE/Batocera-CRT-Script), [batocera-unofficial-addons](https://github.com/batocera-unofficial-addons/batocera-unofficial-addons), [batocera.linux](https://github.com/batocera-linux/batocera.linux), and others.

## Purpose

This repository preserves research, design documents, debug logs, and verdicts for Batocera development efforts. It serves as institutional memory so that future sessions have full context on past decisions, bugs encountered, fixes applied, and lessons learned — across CRT Script, BUA add-ons, storage manager, Wayland/X11, and more.

## Structure

Each top-level directory is a timestamped session covering a specific development effort:

```
YYYY-MM-DD_short-description/
├── design/      — architecture and flow documents
├── research/    — live system findings and technical analysis
├── debug/       — step-by-step test logs and bug investigations
├── plan.md      — implementation plan for the session
└── VERDICT.md   — session retrospective and final assessment
```

Entry names use scope prefixes when helpful (e.g. `bua-steam-*`, `bsm-mergerfs-*`, `crt-*`, `v43-*`).

### VERDICT.md

Each session's `VERDICT.md` is written after development concludes. It captures:

- **Plan vs reality** — how far the shipped code deviated from the original plan
- **Unanticipated bugs** — root causes and fixes
- **Models used** — which AI handled which phases
- **What worked / what didn't** — concrete lessons learned

## How This Is Used

This repository is fed into AI coding assistants (Cursor, Claude, etc.) as context during development. Rather than re-explaining project history each time, the relevant session folder is attached so the model has access to:

- What was tried before and why it failed
- Exact system states (SSH snapshots, log excerpts, config diffs)
- Root causes of past bugs and the fixes that resolved them
- Architectural decisions and reasoning

## Scope

Development efforts documented here include:

- **Batocera-CRT-Script** — CRT/HD mode switching, videomode preservation
- **BUA (batocera-unofficial-addons)** — Steam, Fightcade, add-on fixes
- **batocera.linux** — storage manager, mergerFS, core scripts
- **v43 / Wayland / X11** — display stack, dual-boot, tearing fixes

## Renaming (optional)

The repo was originally Batocera-CRT-Script-RAG. To fully rebrand to Batocera-Development-RAG:

1. **GitHub:** Settings → General → Repository name → `Batocera-Development-RAG`
2. **Local:** `mv Batocera-CRT-Script-RAG Batocera-Development-RAG`
3. **Remote:** `git remote set-url origin <new-URL>` if the clone path changed
4. **Workspace:** Update Cursor/VSCode workspace to reference the new folder path
