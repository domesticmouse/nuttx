# `qemu-rv` Family Boards (`boards/risc-v/qemu-rv`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `qemu-rv` SoC/MCU family under the `risc-v` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`rv-virt`](./rv-virt/README.md) - Board Support Package (BSP) blueprint for `rv-virt` (`risc-v` / `qemu-rv`). Coordinates board initialization, headers, and tooling across `configs, include, kernel, src`. Includes build configurations: `citest`, `citest64`, `elf`, `fb`, `fb64`, `flats` (+31 more).
