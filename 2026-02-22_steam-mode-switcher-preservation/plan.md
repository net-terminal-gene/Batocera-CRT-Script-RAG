# Steam Mode Switcher Preservation

## Problem

BUA (Batocera Unofficial Addons) Steam requires `steam.emulator=sh` and `steam.core=sh` in batocera.conf to run .sh launchers. When users switch between HD and CRT modes via the Mode Switcher, Steam config can be lost and games fail with:

```
error: app/com.valvesoftware.Steam/x86_64/master not installed
```

## Root Cause

The mode switcher uses a **full-file replace** for batocera.conf when restoring. If the target mode's backup was taken before BUA Steam was installed, it has no steam.* lines. Restore overwrites the live file → steam config wiped.

## Solution

Preserve Steam settings across mode switches (same pattern as VNC preservation already in `03_backup_restore.sh`):
- Extract `steam.emulator`, `steam.core`, and all `steam["*.sh"]` keys from source backup or current config
- After batocera.conf restore, re-apply those lines

## Files Touched

| Repo | File | Change |
|------|------|--------|
| Batocera-CRT-Script | `.../mode_switcher_modules/03_backup_restore.sh` | Add Steam preservation block after VNC block in restore_mode_files() |

## Validation

- [ ] Install BUA Steam in HD mode → verify steam.emulator=sh in batocera.conf
- [ ] Run Mode Switcher: HD → CRT → verify Steam launches
- [ ] Run Mode Switcher: CRT → HD → verify steam.* still present, Steam launches
- [ ] Roundtrip; per-game videomode persists
