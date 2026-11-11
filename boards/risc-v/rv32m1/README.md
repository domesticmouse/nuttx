# `rv32m1` Family Boards (`boards/risc-v/rv32m1`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rv32m1` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`rv32m1-vega`](./rv32m1-vega/README.md) - Board Support Package (BSP) blueprint for `rv32m1-vega` (`risc-v` / `rv32m1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `buttons`, `nsh`, `nsh-itcm`.
