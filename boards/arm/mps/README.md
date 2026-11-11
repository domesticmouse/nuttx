# `mps` Family Boards (`boards/arm/mps`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `mps` SoC/MCU family under the `arm` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`mps2-an500`](./mps2-an500/README.md) - Board Support Package (BSP) blueprint for `mps2-an500` (`arm` / `mps`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `nsh`, `xipfs`.
- [`mps2-an521`](./mps2-an521/README.md) - Board Support Package (BSP) blueprint for `mps2-an521` (`arm` / `mps`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `xipfs`.
- [`mps3-an547`](./mps3-an547/README.md) - Board Support Package (BSP) blueprint for `mps3-an547` (`arm` / `mps`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `ap`, `bl`, `clang`, `gcov`, `gdbstub`, `knsh` (+2 more).
