# VERDICT — CRT Tools on Boot Drive (mergerFS Conflict)

## Status: TBD

## Summary

[To be written when implementation is done and validated]

## Root Causes

1. mergerFS `=NC` fix routes new file creates to external drives
2. CRT Tools live under `/userdata/roms/crt/` — within the mergerFS pool
3. Mode switcher requires CRT tools on the boot drive (NVMe/SATA/microSD) during HD/CRT switches (boot-time, external drives may be absent)
4. No per-path exception exists in mergerFS for the crt subdirectory

## Changes Applied

| File | Change |
|------|--------|
| TBD | TBD |
