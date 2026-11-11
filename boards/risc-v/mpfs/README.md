# `mpfs` Family Boards (`boards/risc-v/mpfs`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `mpfs` SoC/MCU family under the `risc-v` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `mpfs`). Coordinates board initialization, headers, and tooling across `kernel, src`.
- [`icicle`](./icicle/README.md) - Board Support Package (BSP) blueprint for `icicle` (`risc-v` / `mpfs`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hwtest`, `knsh`, `nsh`, `opensbi`, `pnsh`, `rpmsg-ch1` (+2 more).
- [`m100pfsevp`](./m100pfsevp/README.md) - Board Support Package (BSP) blueprint for `m100pfsevp` (`risc-v` / `mpfs`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
