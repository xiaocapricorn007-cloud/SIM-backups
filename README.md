# SIM Backups

Private snapshot archive of the SIM UE5 project (`drexon-labs/SIM`).

Each **GitHub Release** is a Phase-N checkpoint of the full UE5 project — `Content/`, `Source/`, `Config/`, `.uproject` — packaged as a `.tar.zst` tarball. Use these to restore a known-good scene state if local work is lost or corrupted.

## What's NOT in the tarballs

The following are excluded because UE regenerates them and they bloat the archive:

- `ue5_project/Saved/` (autosaves, logs)
- `ue5_project/Intermediate/` (build artifacts)
- `ue5_project/Binaries/` (compiled output)
- `ue5_project/DerivedDataCache/`
- `ue5_project/.vscode/`

## Restoring a snapshot

```bash
# Download the tarball from a release, then:
mkdir -p ~/restored-sim
cd ~/restored-sim
tar --use-compress-program='zstd -d' -xf Phase-1-Plains_Lush-2026-04-26.tar.zst
# Open ue5_project/VanguardSim.uproject in UE5 — first launch will regenerate
# Intermediate/ and Saved/ on its own.
```

## Phases

See the [Releases](../../releases) tab. Each release notes summarizes what scene/asset state is captured.

## Why a separate repo

Source-code commits and PRs go to `drexon-labs/SIM` via the normal git flow. This repo exists purely for *full-project binary snapshots* so the team repo stays clean and clones stay fast.
