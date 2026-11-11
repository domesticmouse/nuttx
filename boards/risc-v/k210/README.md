# `k210` Family Boards (`boards/risc-v/k210`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `k210` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`maix-bit`](./maix-bit/README.md) - Board Support Package (BSP) blueprint for `maix-bit` (`risc-v` / `k210`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `elf`, `knsh`, `knsh_smp`, `kostest`, `module`, `nsh` (+3 more).
