# `rx65n` Family Boards (`boards/renesas/rx65n`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `rx65n` SoC/MCU family under the `renesas` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`rx65n`](./rx65n/README.md) - Board Support Package (BSP) blueprint for `rx65n` (`renesas` / `rx65n`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`rx65n-grrose`](./rx65n-grrose/README.md) - Board Support Package (BSP) blueprint for `rx65n-grrose` (`renesas` / `rx65n`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ipv6`, `netnsh`, `nsh`.
- [`rx65n-rsk1mb`](./rx65n-rsk1mb/README.md) - Board Support Package (BSP) blueprint for `rx65n-rsk1mb` (`renesas` / `rx65n`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`.
- [`rx65n-rsk2mb`](./rx65n-rsk2mb/README.md) - Board Support Package (BSP) blueprint for `rx65n-rsk2mb` (`renesas` / `rx65n`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ipv6`, `netnsh`, `nsh`.
