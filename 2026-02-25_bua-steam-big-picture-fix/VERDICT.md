# VERDICT — BUA Steam Big Picture Fix

## Status: TBD

## Summary

[To be written when implementation is complete and validated]

## Root Causes

1. Missing `XAUTHORITY` — wmctrl cannot connect to X11 when Launcher runs from EmulationStation
2. Window title mismatch — Launcher searches for "Steam" only; Big Picture in German is "Big-Picture-Modus"
3. (Optional) Wrong GPU on dual-GPU — Steam defaults to iGPU, rendering fails

## Changes Applied

| File | Change |
|------|--------|
| — | — |
