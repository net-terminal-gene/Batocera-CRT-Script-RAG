# PR Status — HD/CRT Mode Switcher

## PR #390

| Field | Value |
|-------|-------|
| Repo | ZFEbHVUE/Batocera-CRT-Script |
| PR | [#390](https://github.com/ZFEbHVUE/Batocera-CRT-Script/pull/390) |
| Branch | `crt-hd-mode-switcher` → `main` |
| Title | Add HD/CRT Mode Switcher with persistent display configuration |
| Status | **OPEN (Draft)** |
| Created | 2026-01-26 |

## Review Comments

### 1. Backup path (net-terminal-gene, 2026-01-26)

**File:** `Batocera-CRT-Script-v42.sh` (mode backup directory creation)

**Comment:** "Backups need to put into `/userdata/Batocera-CRT-Script-Backup/mode_backups/`"

**Status:** Addressed — backup paths updated from `/userdata/system/Batocera-CRT-Script/mode_backups/` to `/userdata/Batocera-CRT-Script-Backup/mode_backups/`.

---

## Relationship to PR #395

PR #395 (`crt-hd-mode-switcher-v43`) builds on top of PR #390, adding Wayland/X11 dual-boot support for v43 Steam Deck. The `crt-hd-mode-switcher-v43` branch includes the `crt-hd-mode-switcher` commits plus the dual-boot architecture.

**Decision needed:** Close #390 in favor of #395, or merge #390 first then rebase #395.

## Outstanding Items

- [ ] NVIDIA GPU testing
- [ ] Community feedback
- [ ] Decide #390 vs #395 merge order
