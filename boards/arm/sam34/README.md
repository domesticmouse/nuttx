# `sam34` Family Boards (`boards/arm/sam34`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `sam34` SoC/MCU family under the `arm` architecture (8 subdirectories).

## Subdirectories & Boundaries
- [`arduino-due`](./arduino-due/README.md) - Board Support Package (BSP) blueprint for `arduino-due` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh-leds`.
- [`flipnclick-sam3x`](./flipnclick-sam3x/README.md) - Board Support Package (BSP) blueprint for `flipnclick-sam3x` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxlines`.
- [`sam3u-ek`](./sam3u-ek/README.md) - Board Support Package (BSP) blueprint for `sam3u-ek` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `nsh`, `nx`, `nxwm`.
- [`sam4cmp-db`](./sam4cmp-db/README.md) - Board Support Package (BSP) blueprint for `sam4cmp-db` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`sam4e-ek`](./sam4e-ek/README.md) - Board Support Package (BSP) blueprint for `sam4e-ek` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxwm`, `usbnsh`.
- [`sam4l-xplained`](./sam4l-xplained/README.md) - Board Support Package (BSP) blueprint for `sam4l-xplained` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`sam4s-xplained`](./sam4s-xplained/README.md) - Board Support Package (BSP) blueprint for `sam4s-xplained` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`sam4s-xplained-pro`](./sam4s-xplained-pro/README.md) - Board Support Package (BSP) blueprint for `sam4s-xplained-pro` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `fs`, `nsh`.
