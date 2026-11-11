# `cxd56xx` Family Boards (`boards/arm/cxd56xx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `cxd56xx` SoC/MCU family under the `arm` architecture (3 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`arm` / `cxd56xx`). Coordinates board initialization, headers, and tooling across `src`.
- [`drivers`](./drivers/README.md) - Board Support Package (BSP) blueprint for `drivers` (`arm` / `cxd56xx`). Coordinates board initialization, headers, and tooling across `audio, sensors`.
- [`spresense`](./spresense/README.md) - Board Support Package (BSP) blueprint for `spresense` (`arm` / `cxd56xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audio`, `audio_sdk`, `camera`, `charger`, `coremark`, `elf` (+22 more).
