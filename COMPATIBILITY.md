# Compatibility

One row per recorded combination, newest first. The commits are the ones
pinned by this repository at that tag; `git submodule status` on the tag
shows the same list.

Status: **planned** (not built), **bench** (powered and tested on the bench),
**flown**.

| System tag | Date | FW | HW (board revisions) | Mech | Status | Notes |
|---|---|---|---|---|---|---|
| — (first pin, untagged) | 2026-10-31 | `aa16f12` | `9956bfc`: FC rev A (layout 2026-10-24), ESC 1S rev A, GPS rev A, Flow rev A | `739482f` (empty: structure only) | planned | first recording after the move to the ACwing-UAV organization. Board revisions to confirm: the table in the ACwing_HW README lists FC H, ESC B, GPS D, Flow A, while file names and text say rev A everywhere |

## Rules

- A firmware feature that needs a given board revision says so in its
  documentation and here (e.g. "FW ≥ proto-0.2 needs FC rev B: ESC link B").
- A mechanical part names the board revisions it fits in its own README.
- A row moves to **bench** or **flown** only after the test; write what was
  tested in the notes.
