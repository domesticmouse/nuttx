# `imx6` Family Boards (`boards/arm/imx6`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `imx6` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`sabre-6quad`](./sabre-6quad/README.md) - Board Support Package (BSP) blueprint for `sabre-6quad` (`arm` / `imx6`). Coordinates board initialization, headers, and tooling across `configs, include, src`. Includes build configurations: `citest`, `coredump`, `elf`, `knsh`, `knsh_smp`, `libcxx` (+9 more).
