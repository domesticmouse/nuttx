# `gd32f4` Family Boards (`boards/arm/gd32f4`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `gd32f4` SoC/MCU family under the `arm` architecture (5 subdirectories).

## Subdirectories & Boundaries
- [`gd32f450zk-aiotbox`](./gd32f450zk-aiotbox/README.md) - Board Support Package (BSP) blueprint for `gd32f450zk-aiotbox` (`arm` / `gd32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `aiotboxnsh`.
- [`gd32f450zk-eval`](./gd32f450zk-eval/README.md) - Board Support Package (BSP) blueprint for `gd32f450zk-eval` (`arm` / `gd32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `btngpionsh`, `fmcfsnsh`, `fmclfsnsh`, `i2c0testnsh`, `netnsh`, `nsh` (+3 more).
- [`gd32f470ik-eval`](./gd32f470ik-eval/README.md) - Board Support Package (BSP) blueprint for `gd32f470ik-eval` (`arm` / `gd32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `fmclfsnsh`, `i2c0testnsh`, `netnsh`, `nsh`.
- [`gd32f470zk-aiotbox`](./gd32f470zk-aiotbox/README.md) - Board Support Package (BSP) blueprint for `gd32f470zk-aiotbox` (`arm` / `gd32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `aiotboxnsh`.
- [`gd32f470zk-eval`](./gd32f470zk-eval/README.md) - Board Support Package (BSP) blueprint for `gd32f470zk-eval` (`arm` / `gd32f4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `fmclfsnsh`, `i2c0testnsh`, `netnsh`, `nsh`, `sdionsh`, `spilfsnsh`.
