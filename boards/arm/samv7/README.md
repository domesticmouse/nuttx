# `samv7` Family Boards (`boards/arm/samv7`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `samv7` SoC/MCU family under the `arm` architecture (5 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`arm` / `samv7`). Coordinates board initialization, headers, and tooling across `include, src, tools`.
- [`pic32czca70-curiosity`](./pic32czca70-curiosity/README.md) - Board Support Package (BSP) blueprint for `pic32czca70-curiosity` (`arm` / `samv7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `max`, `nsh`.
- [`same70-qmtech`](./same70-qmtech/README.md) - Board Support Package (BSP) blueprint for `same70-qmtech` (`arm` / `samv7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `mcuboot-loader`, `mcuboot-slot-confirm`, `nsh`.
- [`same70-xplained`](./same70-xplained/README.md) - Board Support Package (BSP) blueprint for `same70-xplained` (`arm` / `samv7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `adc`, `can`, `mcuboot-loader`, `mcuboot-slot-confirm`, `mrf24j40-starhub`, `netnsh` (+4 more).
- [`samv71-xult`](./samv71-xult/README.md) - Board Support Package (BSP) blueprint for `samv71-xult` (`arm` / `samv7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `mcuboot-loader`, `mcuboot-slot-confirm`, `mcuboot-swap-test`, `mcuboot-update-agent`, `module` (+8 more).
