# `rm57` Family Boards (`boards/arm/rm57`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rm57` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`rm57l843-launchxl2`](./rm57l843-launchxl2/README.md) - Board Support Package (BSP) blueprint for `rm57l843-launchxl2` (`arm` / `rm57`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `buttons`, `can`, `candma`, `cansock`, `eth` (+9 more).
