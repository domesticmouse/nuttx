# `mx8mp` Family Boards (`boards/arm/mx8mp`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `mx8mp` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`verdin-mx8mp`](./verdin-mx8mp/README.md) - Board Support Package (BSP) blueprint for `verdin-mx8mp` (`arm` / `mx8mp`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `rpmsg`.
