# `rk3399` Family Boards (`boards/arm64/rk3399`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rk3399` SoC/MCU family under the `arm64` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`nanopi_m4`](./nanopi_m4/README.md) - Board Support Package (BSP) blueprint for `nanopi_m4` (`arm64` / `rk3399`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`pinephonepro`](./pinephonepro/README.md) - Board Support Package (BSP) blueprint for `pinephonepro` (`arm64` / `rk3399`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
