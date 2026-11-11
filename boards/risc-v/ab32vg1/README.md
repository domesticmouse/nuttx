# `ab32vg1` Family Boards (`boards/risc-v/ab32vg1`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `ab32vg1` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`ab32vg1-generic`](./ab32vg1-generic/README.md) - Board Support Package (BSP) blueprint for `ab32vg1-generic` (`risc-v` / `ab32vg1`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `ostest`.
