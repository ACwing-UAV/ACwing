<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/ACwing-UAV/ACwing_HW/main/00%20-%20Docs/05%20-%20Brand/ACwing_logo_white.png">
    <img alt="ACwing" src="https://raw.githubusercontent.com/ACwing-UAV/ACwing_HW/main/00%20-%20Docs/05%20-%20Brand/ACwing_logo_black.png" width="260">
  </picture>
</p>

<h1 align="center">ACwing – open drone platform</h1>

<p align="center">
  Flight controller, power and expansion boards, firmware, tools and mechanics for small multirotors<br>
  by Andrea Cirillo
</p>

---

This is the **system repository** of ACwing. It holds no design files of its
own: it pins one commit of each part of the project, so that a commit (or a
tag) of this repository names a set of firmware, hardware and mechanics that
belong together.

| Folder | Repository | What |
|---|---|---|
| [`fw/`](https://github.com/ACwing-UAV/ACwing_FW) | ACwing_FW | flight-controller firmware (STM32WB55), Flow bridge firmware (STM32C011), PC tools in MATLAB and Python, ACwing Pilot app. Documentation: [acwing-uav.github.io/ACwing_FW](https://acwing-uav.github.io/ACwing_FW/) |
| [`hw/`](https://github.com/ACwing-UAV/ACwing_HW) | ACwing_HW | KiCad projects and manufacturing files: FC, ESC 1S, GPS, Flow; system and stack documents |
| [`mech/`](https://github.com/ACwing-UAV/ACwing_Mechs) | ACwing_Mechs | frames, mounts, printed parts |

Which versions work together, and what was tested: [COMPATIBILITY.md](COMPATIBILITY.md).

## Getting the whole project

```
git lfs install                       # once: the mechanics use Git LFS
git clone --recursive https://github.com/ACwing-UAV/ACwing.git
```

Already cloned without `--recursive`:

```
git submodule update --init
```

Each folder is then a normal clone of its repository, checked out at the
pinned commit (detached HEAD). To work in one of them, check out a branch
first: `cd fw && git switch main`.

## Working on the project

Day-to-day work happens **in the individual repositories**, not here. This
repository moves only when a combination of versions is worth recording:

1. Commit and push in `fw/`, `hw/` or `mech/` (or work in a separate clone of
   that repository).
2. When the new combination has been checked, record it here:
   ```
   git submodule update --remote fw    # or hw, mech: moves to the tip of main
   git add fw
   git commit -m "fw: <what changed>"
   ```
3. Update [COMPATIBILITY.md](COMPATIBILITY.md) in the same commit, and tag the
   milestones (`git tag proto-0.2`).

Dependabot opens a pull request here every week when one of the three
repositories has moved ahead ([`.github/dependabot.yml`](.github/dependabot.yml)):
merge it when the combination has been checked, close it otherwise.

## Interfaces between the parts

Each interface has **one owner**, the repository that produces it; the others
link to it and never keep a copy.

| Interface | Owner | File |
|---|---|---|
| FC pin map (MCU pins ↔ connectors) | hw → used by fw | [`hw/00 - Docs/00 - FC_Docs/ACwing_FC_A_pinmap.md`](https://github.com/ACwing-UAV/ACwing_HW/blob/main/00%20-%20Docs/00%20-%20FC_Docs/ACwing_FC_A_pinmap.md) |
| FC outline and holes (DXF) | hw → used by mech | [`hw/00 - Docs/00 - FC_Docs/ACwing_FC_A_outline.dxf`](https://github.com/ACwing-UAV/ACwing_HW/blob/main/00%20-%20Docs/00%20-%20FC_Docs/ACwing_FC_A_outline.dxf) |
| Flow board outline (DXF) | hw → used by mech | [`hw/00 - Docs/03 - FLOW_Docs/ACwing_Flow_A_mech_outline.dxf`](https://github.com/ACwing-UAV/ACwing_HW/blob/main/00%20-%20Docs/03%20-%20FLOW_Docs/ACwing_Flow_A_mech_outline.dxf) |
| Board 3D models (STEP) | hw → used by mech | `hw/00 - Docs/<board>_Docs/<board>.step` |
| Stack, mechanical handoff, frame answers | hw ↔ mech | [`hw/00 - Docs/04 - System_Docs`](https://github.com/ACwing-UAV/ACwing_HW/tree/main/00%20-%20Docs/04%20-%20System_Docs) |
| ACwing Pilot protocol v2 | fw → used by the app | [`fw/03 - Docs/firmware/protocol-v2.md`](https://github.com/ACwing-UAV/ACwing_FW/blob/main/03%20-%20Docs/firmware/protocol-v2.md) |

The links point to `main` of each repository; after a recursive clone the same
files are under `hw/` and `fw/` at the pinned commit.

## License

[MIT](LICENSE) for this repository; each submodule carries its own license.
