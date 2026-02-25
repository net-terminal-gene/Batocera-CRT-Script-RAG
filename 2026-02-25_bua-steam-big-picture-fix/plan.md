# BUA Steam Big Picture Fix

## Agent/Model Scope

Composer + batocera-unofficial-addons repo. Source: [HOW-TO] Fix Steam Big Picture Mode in Batocera PDF (Steam black screen / returns to menu when launching from EmulationStation).

## Problem

Steam Big Picture Mode launched from Batocera EmulationStation either returns immediately to the menu or shows a black screen with a mouse cursor. Launching via SSH works fine. Affects Batocera 42 on systems with AMD Renoir iGPU + RX 6600 XT (and potentially other dual-GPU or non-English locales).

## Root Cause

Three issues identified in the PDF:

1. **Missing XAUTHORITY** — wmctrl cannot connect to X11 without `XAUTHORITY`; fails with "Cannot open display", times out, returns to menu
2. **Localized window title** — Launcher searches for "Steam" only; Big Picture window in German (and other locales) is titled "Big-Picture-Modus"
3. **Wrong GPU on dual-GPU** — Steam defaults to iGPU; rendering fails, Steam exits after ~13 seconds (optional/configurable fix)

## Solution

| Change | File | Effort |
|--------|------|--------|
| Add `export XAUTHORITY=/var/run/xauth` | `steam/extra/Launcher` | 1 line |
| Add `export RIM_ALLOW_ROOT=1` and `export HOME=/userdata/system/add-ons/steam` (Steam runtime compatibility; Launcher2 has these) | `steam/extra/Launcher` | 2 lines |
| Broaden wmctrl regex to match localized titles: replace `grep -qi "Steam"` with `grep -qiE "Steam|Big.Picture|Big-Picture"` in both wait loop and monitor loop | `steam/extra/Launcher` | 2 replacements |
| Align TIMEOUT with Launcher2/PDF: 240 seconds (Launcher currently uses 60) | `steam/extra/Launcher` | 1 line |
| DRI_PRIME config (optional / deferred) — config file or auto-detect for dual-GPU; doc-only if not implemented | TBD | Medium |
| Hide ES / fullscreen Steam (optional / deferred) — PDF has these; `wmctrl -r "Big-Picture"` fails on localized titles, would need broader match | `steam/extra/Launcher` | Low–medium |

## Files Touched

| Repo | File | Change |
|------|------|--------|
| batocera-unofficial-addons | `steam/extra/Launcher` | Add XAUTHORITY, RIM_ALLOW_ROOT, HOME; broaden wmctrl regex (2 places); TIMEOUT=240 |

## Out of Scope (this iteration)

- **lbfix.sh** — Launcher2 invokes it; Launcher does not. Not in PDF fix; leave as-is.
- **DRI_PRIME** — Deferred unless dual-GPU users report; config file approach if needed later.
- **Hide ES / fullscreen** — Deferred; requires localized wmctrl match if we add it.

## Validation

- [ ] Launch Steam Big Picture from Ports menu — does not return immediately to menu
- [ ] Steam Big Picture displays (no black screen)
- [ ] Test on German (or other non-English) Batocera locale — window detection works
- [ ] On dual-GPU AMD systems: verify Steam uses dGPU (or document DRI_PRIME config)
