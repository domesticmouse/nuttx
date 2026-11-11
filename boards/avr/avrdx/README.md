# `avrdx` Family Boards (`boards/avr/avrdx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `avrdx` SoC/MCU family under the `avr` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`breadxavr`](./breadxavr/README.md) - Board Support Package (BSP) blueprint for `breadxavr` (`avr` / `avrdx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ws2812`.
