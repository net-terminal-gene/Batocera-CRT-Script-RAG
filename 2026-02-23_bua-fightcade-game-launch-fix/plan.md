# BUA Fightcade Game Launch Fix

## Agent/Model Scope

Composer + ssh-batocera skill for live diagnostics on Batocera hardware.

## Problem

BUA (batocera-unofficial-addons) Fightcade installs and launches correctly — login works — but loading a game fails. The Flatpak version of Fightcade works end-to-end on the same system, including game launch.

## Root Cause

TBD — to be determined via step-by-step observation comparing BUA vs Flatpak behavior.

## Solution

TBD — pending root cause identification.

## Files Touched

| Repo | File | Change |
|------|------|--------|
| batocera-unofficial-addons | fightcade/fightcade.sh | BUA installer |
| batocera-unofficial-addons | fightcade/sym_wine.sh | Wine symlink manager |
| (on Batocera) | /userdata/roms/ports/Fightcade.sh | Generated port launcher |

## Validation

- [ ] BUA Fightcade launches successfully
- [ ] Login works
- [ ] Joining a game room works
- [ ] Game loads and emulator starts
- [ ] Compare behavior matches Flatpak version
