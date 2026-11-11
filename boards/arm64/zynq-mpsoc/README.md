# `zynq-mpsoc` Family Boards (`boards/arm64/zynq-mpsoc`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `zynq-mpsoc` SoC/MCU family under the `arm64` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`zcu111`](./zcu111/README.md) - Board Support Package (BSP) blueprint for `zcu111` (`arm64` / `zynq-mpsoc`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jtag`, `netjtag`, `netnsh`, `nsh`.
