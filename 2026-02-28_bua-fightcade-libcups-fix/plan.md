# BUA Fightcade libcups Fix

## Agent/Model Scope

Composer + ssh-batocera skill for remote verification.

## Problem

BUA Fightcade (fc2-electron) fails to launch with:

```
./fc2-electron/fc2-electron: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory
```

Batocera does not include libcups in its base system. The fc2-electron binary (Electron-based Fightcade 2 UI) requires it.

## Root Cause

The Fightcade port launcher did not set `LD_LIBRARY_PATH`. The BUA ecosystem provides `libcups.so.2` in `/userdata/system/add-ons/.dep/` (when Chrome or another add-on is installed), but the dynamic linker could not find it because the launcher never pointed to that directory.

## Solution

Add `LD_LIBRARY_PATH` to the generated port launcher so fc2-electron inherits it and finds libcups in `.dep`:

```bash
export LD_LIBRARY_PATH="/userdata/system/add-ons/.dep:${LD_LIBRARY_PATH}"
```

## Files Touched

| Repo | File | Change |
|------|------|--------|
| batocera-unofficial-addons | fightcade/fightcade.sh | Add LD_LIBRARY_PATH export in port launcher template |

## Validation

- [x] Remote patch applied to `/userdata/roms/ports/Fightcade.sh`; fc2-electron launches
- [x] Change added to fightcade.sh in BUA repo; survives reinstall
