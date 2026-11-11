# `qemu` Family Boards (`boards/x86_64/qemu`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `qemu` SoC/MCU family under the `x86_64` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`qemu-intel64`](./qemu-intel64/README.md) - Board Support Package (BSP) blueprint for `qemu-intel64` (`x86_64` / `qemu`). Coordinates board initialization, headers, and tooling across `configs, include, src`. Includes build configurations: `citest_smp`, `earlyfb`, `fb`, `jumbo`, `knsh_romfs`, `knsh_romfs_pci` (+9 more).
