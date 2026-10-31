<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/ACwing-UAV/ACwing/main/brand/ACwing_logo_white.png">
    <img alt="ACwing" src="https://raw.githubusercontent.com/ACwing-UAV/ACwing/main/brand/ACwing_logo_black.png" width="240">
  </picture>
</p>

<p align="center">
  <b>Open drone platform for small multirotors</b><br>
  flight controller · power and expansion boards · firmware · tools · mechanics
</p>

---

ACwing is a modular set of open boards, firmware and frames. A universal
**flight controller** (STM32WB55, IMU, barometer, compass, BLE) drives a 1S
brushed power board or commercial 4-in-1 ESCs; optional **GNSS** and
**optical-flow** boards plug into its Qwiic ports. The firmware estimates the
attitude with an invariant EKF on SO(3) and talks to the **ACwing Pilot** app
over BLE.

## Repositories

| | Repository | What |
|---|---|---|
| 🧭 | [**ACwing**](https://github.com/ACwing-UAV/ACwing) | start here: the three repositories below as submodules, the versions that belong together, brand files |
| 🔌 | [ACwing_HW](https://github.com/ACwing-UAV/ACwing_HW) | KiCad projects and JLCPCB files: FC, ESC 1S, GPS, Flow |
| 💾 | [ACwing_FW](https://github.com/ACwing-UAV/ACwing_FW) | firmware, MATLAB and Python tools, ACwing Pilot app · [documentation](https://acwing-uav.github.io/ACwing_FW/) |
| 🛠️ | [ACwing_Mechs](https://github.com/ACwing-UAV/ACwing_Mechs) | frames, mounts, printed parts |

```
git lfs install
git clone --recursive https://github.com/ACwing-UAV/ACwing.git
```

## Status

| Track | Where it is |
|---|---|
| Hardware | FC, ESC 1S, GPS, Flow at **rev A**: routed, 0 DRC errors, not produced yet |
| Firmware | attitude IEKF validated on the board; BLE telemetry on the board; protocol v2, altitude, Flow, battery, flight log host-tested |
| Mechanics | frame for the rev A stack in progress |
| Next | order rev A → bench bring-up → firmware port to the ACwing FC → control loops and first flight |

Progress is tracked in the [project board](https://github.com/orgs/ACwing-UAV/projects)
with four milestones shared by all repositories:
**Rev A – order** → **Rev A – bring-up** → **Phase 2 on the board** → **Phase 3 – first flight**.

<sub>by Andrea Cirillo</sub>
