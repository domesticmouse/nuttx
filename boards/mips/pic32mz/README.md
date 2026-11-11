# `pic32mz` Family Boards (`boards/mips/pic32mz`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `pic32mz` SoC/MCU family under the `mips` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`chipkit-wifire`](./chipkit-wifire/README.md) - Board Support Package (BSP) blueprint for `chipkit-wifire` (`mips` / `pic32mz`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`ev49n51a`](./ev49n51a/README.md) - Board Support Package (BSP) blueprint for `ev49n51a` (`mips` / `pic32mz`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `bridge`, `netnsh`, `nsh`, `wlan`.
- [`flipnclick-pic32mz`](./flipnclick-pic32mz/README.md) - Board Support Package (BSP) blueprint for `flipnclick-pic32mz` (`mips` / `pic32mz`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxlines`.
- [`pic32mz-starterkit`](./pic32mz-starterkit/README.md) - Board Support Package (BSP) blueprint for `pic32mz-starterkit` (`mips` / `pic32mz`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
