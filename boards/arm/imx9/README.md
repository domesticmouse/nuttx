# `imx9` Family Boards (`boards/arm/imx9`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `imx9` SoC/MCU family under the `arm` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`imx93-qsb`](./imx93-qsb/README.md) - Board Support Package (BSP) blueprint for `imx93-qsb` (`arm` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `nsh-ddr`, `rpmsg`.
- [`imx95-evk`](./imx95-evk/README.md) - Board Support Package (BSP) blueprint for `imx95-evk` (`arm` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `nsh`, `rpmsg`.
- [`mr-navq95b`](./mr-navq95b/README.md) - Board Support Package (BSP) blueprint for `mr-navq95b` (`arm` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `rpmsg`.
