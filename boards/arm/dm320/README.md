# `dm320` Family Boards (`boards/arm/dm320`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `dm320` SoC/MCU family under the `arm` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`ntosd-dm320`](./ntosd-dm320/README.md) - Board Support Package (BSP) blueprint for `ntosd-dm320` (`arm` / `dm320`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nettest`, `nsh`, `poll`, `udp`, `webserver`.
