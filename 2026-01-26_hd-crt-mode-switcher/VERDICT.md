# VERDICT — HD/CRT Mode Switcher

## Status: OPEN (PR #390 — Draft)

## Summary

Complete HD/CRT mode switching system implemented with overlay file swapping, full state preservation (batocera.conf, MAME, RetroArch, scripts, video settings), controller-friendly UI, and modular architecture. Tested on AMD GPU and Steam Deck. Pending NVIDIA testing and community feedback.

## Root Causes (of the original problem)

1. No infrastructure for switching between HD and CRT display configurations
2. Overlay editing (vs swapping) left mixed state between modes
3. No backup/restore for per-mode emulator configs (MAME TATE/YOKO, RetroArch CRT timing)

## Changes Applied

| File | Change |
|------|--------|
| `mode_switcher.sh` | Main orchestrator |
| `mode_switcher_modules/01-04` | Detection, output selection, backup/restore, UI |
| `Batocera-CRT-Script-v42.sh` | Mode Switcher install integration |
| `crt/mode_switcher.sh` + `.keys` | CRT Tools launcher wrapper |
| `crt/gamelist.xml` + `crt/images/` | ES game carousel entries and art |
