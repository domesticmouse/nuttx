# `kinetis` Family Boards (`boards/arm/kinetis`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `kinetis` SoC/MCU family under the `arm` architecture (7 subdirectories).

## Subdirectories & Boundaries
- [`freedom-k28f`](./freedom-k28f/README.md) - Board Support Package (BSP) blueprint for `freedom-k28f` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nshsdusb`.
- [`freedom-k64f`](./freedom-k64f/README.md) - Board Support Package (BSP) blueprint for `freedom-k64f` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `cdcacm`, `demo`, `netnsh`, `nsh`.
- [`freedom-k66f`](./freedom-k66f/README.md) - Board Support Package (BSP) blueprint for `freedom-k66f` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`.
- [`kwikstik-k40`](./kwikstik-k40/README.md) - Board Support Package (BSP) blueprint for `kwikstik-k40` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ostest`.
- [`teensy-3.x`](./teensy-3.x/README.md) - Board Support Package (BSP) blueprint for `teensy-3.x` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`.
- [`twr-k60n512`](./twr-k60n512/README.md) - Board Support Package (BSP) blueprint for `twr-k60n512` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`twr-k64f120m`](./twr-k64f120m/README.md) - Board Support Package (BSP) blueprint for `twr-k64f120m` (`arm` / `kinetis`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`.
