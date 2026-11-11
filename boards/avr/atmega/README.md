# `atmega` Family Boards (`boards/avr/atmega`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `atmega` SoC/MCU family under the `avr` architecture (5 subdirectories).

## Subdirectories & Boundaries
- [`amber`](./amber/README.md) - Board Support Package (BSP) blueprint for `amber` (`avr` / `atmega`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`.
- [`arduino-mega2560`](./arduino-mega2560/README.md) - Board Support Package (BSP) blueprint for `arduino-mega2560` (`avr` / `atmega`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`.
- [`elegoo-mega2560r3`](./elegoo-mega2560r3/README.md) - Board Support Package (BSP) blueprint for `elegoo-mega2560r3` (`avr` / `atmega`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`mega1284p-xplained`](./mega1284p-xplained/README.md) - Board Support Package (BSP) blueprint for `mega1284p-xplained` (`avr` / `atmega`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`.
- [`moteino-mega`](./moteino-mega/README.md) - Board Support Package (BSP) blueprint for `moteino-mega` (`avr` / `atmega`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`.
