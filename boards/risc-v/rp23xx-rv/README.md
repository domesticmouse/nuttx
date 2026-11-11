# `rp23xx-rv` Family Boards (`boards/risc-v/rp23xx-rv`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rp23xx-rv` SoC/MCU family under the `risc-v` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`common`](./common/README.md) - Board Support Package (BSP) blueprint for `common` (`risc-v` / `rp23xx-rv`). Coordinates board initialization, headers, and tooling across `include, src`.
- [`raspberrypi-pico-2-rv`](./raspberrypi-pico-2-rv/README.md) - Board Support Package (BSP) blueprint for `raspberrypi-pico-2-rv` (`risc-v` / `rp23xx-rv`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh-smp`, `usbnsh`, `usbnsh-smp`.
