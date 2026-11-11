# `sama5` Family Boards (`boards/arm/sama5`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `sama5` SoC/MCU family under the `arm` architecture (6 subdirectories).

## Subdirectories & Boundaries
- [`giant-board`](./giant-board/README.md) - Board Support Package (BSP) blueprint for `giant-board` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `helpers, include, src`. Includes build configurations: `netnsh`, `nsh`, `sdmmc-net-nsh`, `sdmmcnsh`.
- [`jupiter-nano`](./jupiter-nano/README.md) - Board Support Package (BSP) blueprint for `jupiter-nano` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`, `sdmmc-nsh-net-resolvconf`, `sdmmcnsh`.
- [`sama5d2-xult`](./sama5d2-xult/README.md) - Board Support Package (BSP) blueprint for `sama5d2-xult` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`, `sdmmcnsh`.
- [`sama5d3-xplained`](./sama5d3-xplained/README.md) - Board Support Package (BSP) blueprint for `sama5d3-xplained` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `helpers, include, src`. Includes build configurations: `bluetooth`, `bridge`, `ethernet-over-usb-2-high-speed`, `knsh`, `nsh`.
- [`sama5d3x-ek`](./sama5d3x-ek/README.md) - Board Support Package (BSP) blueprint for `sama5d3x-ek` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `demo`, `hello`, `norboot`, `nsh`, `nx`, `nxplayer` (+2 more).
- [`sama5d4-ek`](./sama5d4-ek/README.md) - Board Support Package (BSP) blueprint for `sama5d4-ek` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `at25boot`, `bridge`, `dramboot`, `elf`, `ipv6`, `knsh` (+3 more).
