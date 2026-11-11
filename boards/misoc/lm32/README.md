# `lm32` Family Boards (`boards/misoc/lm32`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `lm32` SoC/MCU family under the `misoc` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`misoc`](./misoc/README.md) - Board Support Package (BSP) blueprint for `misoc` (`misoc` / `lm32`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`.
