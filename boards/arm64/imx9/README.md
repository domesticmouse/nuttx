# `imx9` Family Boards (`boards/arm64/imx9`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `imx9` SoC/MCU family under the `arm64` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`imx93-evk`](./imx93-evk/README.md) - Board Support Package (BSP) blueprint for `imx93-evk` (`arm64` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `bootloader`, `knsh`, `koptee`, `nsh`, `optee`.
- [`imx95-a55-evk`](./imx95-a55-evk/README.md) - Board Support Package (BSP) blueprint for `imx95-a55-evk` (`arm64` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `emmc`, `nsh`.
