# VERDICT — batocera-storage-manager mergerFS =NC Fix

## Status: TBD

## Summary

[To be written when PR is submitted and validated]

## Root Causes

1. `batocera-storage-manager` builds the mergerFS pool without `=NC` (No Create) on the internal NVMe base directory (`/userdata/.roms_base`)
2. `category.create=mfs` (Most Free Space) policy causes new file writes to land on whichever branch has the most free space — including NVMe, creating full duplicate copies alongside the external drive copies
3. `moveonenospc=true` provides an additional pathway for files to migrate to NVMe on write failures
4. `S12mergerfs` (the manual config path) correctly uses `=NC` but the storage manager never adopted the same pattern
5. Cross-drive comparison via SSH vs macOS `ls` produced false 0% overlap results due to filename encoding differences — actual overlap was 100% (all NVMe copies were duplicates, confirmed via FileZilla transfer test)

## Known Blocker: Steam Launcher Conflict

A blanket `=NC` on the NVMe branch breaks Steam game installs. When a new Steam game is installed, Batocera creates a `.sh` launcher in `/userdata/roms/steam/` — which goes through mergerFS. With `=NC` on NVMe, the launcher gets routed to an external drive instead, causing it to disappear when the drive isn't connected.

- Confirmed: all existing Steam launchers are physically on `nvme0n1p2` (`stat` → `Device: 259,2`)
- mergerFS has no per-subdirectory branch mode — `=NC` applies to the entire NVMe branch
- Fix requires either moving Steam launchers outside the mergerFS pool, or writing them directly to the physical NVMe path, bypassing the pool
- See `design/README.md` → "Candidate Solutions for Steam Conflict" for options

## Changes Applied

| File | Change |
|------|--------|
| `package/batocera/core/batocera-scripts/scripts/batocera-storage-manager` | Add `=NC` to `BASE_DIR` in all mergerFS branch string constructions (~lines 637, 807, 895) |
