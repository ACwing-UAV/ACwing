# Compatibility

One row per recorded combination, newest first. The commits are the ones
pinned by this repository at that tag; `git submodule status` on the tag
shows the same list.

Status: **planned** (not built), **bench** (powered and tested on the bench),
**flown**.

| System tag | Date | FW | HW (board revisions) | Mech | Status | Notes |
|---|---|---|---|---|---|---|
| — (untagged) | 2026-10-31 | `a01e832` | `0562ac6`: FC, ESC 1S, GPS, Flow all **rev A** (layout 2026-10-24) | `f63c727` (structure only) | planned | no PCB produced yet. Brand files moved to `brand/` of this repository |
| — (first pin, untagged) | 2026-10-31 | `aa16f12` | `9956bfc` | `739482f` | superseded | `9956bfc` had KiCad `.history` gitlinks that break `git clone --recursive` |

## Rules

- A firmware feature that needs a given board revision says so in its
  documentation and here (e.g. "FW ≥ proto-0.2 needs FC rev B: ESC link B").
- A mechanical part names the board revisions it fits in its own README.
- A row moves to **bench** or **flown** only after the test; write what was
  tested in the notes.
