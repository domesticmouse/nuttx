# `qemu` Family Boards (`boards/arm64/qemu`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `qemu` SoC/MCU family under the `arm64` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`qemu-armv8a`](./qemu-armv8a/README.md) - Board Support Package (BSP) blueprint for `qemu-armv8a` (`arm64` / `qemu`). Coordinates board initialization, headers, and tooling across `configs, include, src`. Includes build configurations: `citest`, `citest_smp`, `fastboot`, `fb`, `gdbstub`, `knsh` (+17 more).
