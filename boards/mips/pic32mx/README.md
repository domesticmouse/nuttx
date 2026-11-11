# `pic32mx` Family Boards (`boards/mips/pic32mx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `pic32mx` SoC/MCU family under the `mips` architecture (5 subdirectories).

## Subdirectories & Boundaries
- [`mirtoo`](./mirtoo/README.md) - Board Support Package (BSP) blueprint for `mirtoo` (`mips` / `pic32mx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxffs`.
- [`pic32mx-starterkit`](./pic32mx-starterkit/README.md) - Board Support Package (BSP) blueprint for `pic32mx-starterkit` (`mips` / `pic32mx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh2`.
- [`pic32mx7mmb`](./pic32mx7mmb/README.md) - Board Support Package (BSP) blueprint for `pic32mx7mmb` (`mips` / `pic32mx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`sure-pic32mx`](./sure-pic32mx/README.md) - Board Support Package (BSP) blueprint for `sure-pic32mx` (`mips` / `pic32mx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`.
- [`ubw32`](./ubw32/README.md) - Board Support Package (BSP) blueprint for `ubw32` (`mips` / `pic32mx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
