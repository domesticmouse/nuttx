# `gd32w51x` Family Boards (`boards/arm/gd32w51x`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `gd32w51x` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`gd-xd-w515-eval`](./gd-xd-w515-eval/README.md) - Board Support Package (BSP) blueprint for `gd-xd-w515-eval` (`arm` / `gd32w51x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `littlefs`, `nsh`, `ostest`, `periph`, `pm`.
