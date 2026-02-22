# Batocera-CRT-Script-RAG

Historical reference archive for the [Batocera-CRT-Script](https://github.com/ZFEbHVUE/Batocera-CRT-Script) project.

## Purpose

This repository preserves all research, design documents, debug logs, and test results generated during development of the Batocera CRT Script. It serves as a retrieval-augmented knowledge base so that future development sessions have full context on past decisions, bugs encountered, fixes applied, and lessons learned.

## Structure

Each top-level directory is a timestamped session covering a specific development effort:

```
YYYY-MM-DD_short-description/
├── design/      — architecture and flow documents
├── research/    — live system findings and technical analysis
├── debug/       — step-by-step test logs and bug investigations
└── plan.md      — implementation plan for the session
```

## How This Is Used

This repository is designed to be fed into AI coding assistants (Cursor, Claude, etc.) as context during development sessions. Rather than re-explaining the entire project history each time, the relevant session folder is attached or referenced so the model has immediate access to:

- What was tried before and why it failed
- Exact system states at each step (SSH snapshots, log excerpts, config diffs)
- Root causes of past bugs and the fixes that resolved them
- Architectural decisions and the reasoning behind them

This eliminates repeated debugging of the same issues and gives the AI model the equivalent of institutional memory for the project.

## Why This Exists

The Batocera CRT Script involves complex interactions between Syslinux boot configurations, OverlayFS persistence, X11/Wayland display stacks, and Batocera's emulatorlauncher pipeline. Bugs are often subtle (e.g., video mode string precision mismatches) and require systematic documentation to diagnose and prevent regressions. This archive ensures that knowledge is never lost between sessions.
