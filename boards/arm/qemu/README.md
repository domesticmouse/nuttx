# `qemu` Family Boards (`boards/arm/qemu`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `qemu` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`qemu-armv7a`](./qemu-armv7a/README.md) - Board Support Package (BSP) blueprint for `qemu-armv7a` (`arm` / `qemu`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `full`, `gdbstub`, `knsh`, `knsh_smp`, `nsh`, `rpproxy` (+2 more).
- [`qemu-armv7r`](./qemu-armv7r/README.md) - Board Support Package (BSP) blueprint for `qemu-armv7r` (`arm` / `qemu`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `nsh`, `pnsh`.
