# VERDICT — BUA Steam Per-Game VIDEO MODE Fix

## Status: FIXED (batocera-unofficial-addons)

## Summary

Per-game VIDEO MODE for BUA Steam games was not applied because configgen looked up settings under `ports["rom"]` instead of `steam["rom"]`, and used the Flatpak steam generator instead of the sh generator. Fix applied in `batocera-unofficial-addons` branch `fix-steam-videomode` (commit 40f8317).

## Root Causes

1. **`es_systems_steam.cfg`** used `-system ports -systemname ports` → configgen read `ports["game.sh"]`, not `steam["game.sh"]`
2. **Emulator** was `steam` (Flatpak) instead of `sh` → ran batocera-steam without steam.emulator=sh
3. **Duplicate videomode** in `es_features_steam.cfg` → double VIDEO MODE in EmulationStation

## Changes Applied

| File | Change |
|------|--------|
| `steam/extra/es_systems_steam.cfg` | -system steam, sh emulator |
| `steam/extra/es_features_steam.cfg` | Removed videomode from features |
| `steam/steam.sh` | Add steam.emulator=sh, steam.core=sh on install |

## Open Item: steam2.sh

BUA UI uses `steam2.sh`, not `steam.sh`. Ensure `steam2.sh` gains the same batocera.conf write logic before PR merge.
