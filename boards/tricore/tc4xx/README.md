# `tc4xx` Family Boards (`boards/tricore/tc4xx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `tc4xx` SoC/MCU family under the `tricore` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`triboard_tc4x9_com`](./triboard_tc4x9_com/README.md) - Board Support Package (BSP) blueprint for `triboard_tc4x9_com` (`tricore` / `tc4xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
