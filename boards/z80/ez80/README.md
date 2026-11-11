# `ez80` Family Boards (`boards/z80/ez80`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `ez80` SoC/MCU family under the `z80` architecture (4 subdirectories).

## Subdirectories & Boundaries
- [`ez80f910200kitg`](./ez80f910200kitg/README.md) - Board Support Package (BSP) blueprint for `ez80f910200kitg` (`z80` / `ez80`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ostest`.
- [`ez80f910200zco`](./ez80f910200zco/README.md) - Board Support Package (BSP) blueprint for `ez80f910200zco` (`z80` / `ez80`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `dhcpd`, `httpd`, `nettest`, `nsh`, `poll`.
- [`makerlisp`](./makerlisp/README.md) - Board Support Package (BSP) blueprint for `makerlisp` (`z80` / `ez80`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh_flash`, `nsh_ram`, `sdboot`.
- [`z20x`](./z20x/README.md) - Board Support Package (BSP) blueprint for `z20x` (`z80` / `ez80`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`, `sdboot`, `w25boot`.
