# `at32` Family Boards (`boards/arm/at32`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `at32` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`at32f437-mini`](./at32f437-mini/README.md) - Board Support Package (BSP) blueprint for `at32f437-mini` (`arm` / `at32`). Coordinates board initialization, headers, and tooling across `include, kernel, src, tool`. Includes build configurations: `adc`, `can_char`, `can_socket`, `eth`, `msc`, `nsh` (+6 more).
