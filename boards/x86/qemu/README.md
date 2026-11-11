# `qemu` Family Boards (`boards/x86/qemu`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `qemu` SoC/MCU family under the `x86` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`qemu-i486`](./qemu-i486/README.md) - Board Support Package (BSP) blueprint for `qemu-i486` (`x86` / `qemu`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `ostest`, `vga_fb`.
