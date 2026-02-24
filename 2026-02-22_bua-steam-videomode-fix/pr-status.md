# PR Status — BUA Steam Per-Game VIDEO MODE Fix

## PR

| Field | Value |
|-------|-------|
| Repo | batocera-unofficial-addons/batocera-unofficial-addons |
| PR | [#142](https://github.com/batocera-unofficial-addons/batocera-unofficial-addons/pull/142) |
| Branch | `fix-steam-videomode` |
| Title | Fix Steam VIDEO MODE: use steam system + sh emulator for per-game videomode |
| Status | **MERGED** |
| Merged | 2026-02-23 |

## Review / Comments

No review comments or change requests were posted. PR was merged without modifications.

## Changes Included

| File | Change |
|------|--------|
| `steam/extra/es_systems_steam.cfg` | `-system steam`, `sh` emulator |
| `steam/extra/es_features_steam.cfg` | Removed duplicate `videomode` from features |
| `steam/steam.sh` | Add `steam.emulator=sh`, `steam.core=sh` to batocera.conf on install |

## Post-Merge Notes

- The `steam2.sh` open item from VERDICT.md (BUA UI installer path) was not addressed in this PR. Needs follow-up if `steam2.sh` is the primary install path for some users.
