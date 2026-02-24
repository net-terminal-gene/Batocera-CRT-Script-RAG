# PR Status — v43 Wayland/X11 Dual-Boot Support

## PRs

### PR #395 (active — dual-boot v43)

| Field | Value |
|-------|-------|
| Repo | ZFEbHVUE/Batocera-CRT-Script |
| PR | [#395](https://github.com/ZFEbHVUE/Batocera-CRT-Script/pull/395) |
| Branch | `crt-hd-mode-switcher-v43` → `main` |
| Title | Add Wayland/X11 dual-boot support with HD↔CRT mode switching |
| Status | **OPEN (Draft)** |
| Created | 2026-02-22 |

#### Review / Comments

No review comments or change requests posted yet.

#### Key Commits

- `addfd05` — Add Wayland/X11 dual-boot support with HD↔CRT mode switching

---

### PR #390 (predecessor — mode switcher base)

See dedicated RAG entry: [`2026-01-26_hd-crt-mode-switcher/`](../2026-01-26_hd-crt-mode-switcher/)

PR #390 is the original mode switcher PR. PR #395 builds on top of it with the v43 Wayland/X11 dual-boot architecture. Both are currently open drafts.

---

## Outstanding Items

- [ ] Steam preservation module (`steam_preservation.sh`) — implemented but not yet tested on device
- [ ] `steam2.sh` open item from BUA Steam fix (ensure batocera.conf writes)
- [ ] Steam videomode precision mismatch on CRT — user workaround is to set a distinct resolution (e.g. `768x576`); root fix for "Auto" mode TBD
- [ ] PR #390 — determine whether to close in favor of #395, or merge #390 first then #395
