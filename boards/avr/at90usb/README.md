# `at90usb` Family Boards (`boards/avr/at90usb`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `at90usb` SoC/MCU family under the `avr` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`micropendous3`](./micropendous3/README.md) - Board Support Package (BSP) blueprint for `micropendous3` (`avr` / `at90usb`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`.
- [`teensy-2.0`](./teensy-2.0/README.md) - Board Support Package (BSP) blueprint for `teensy-2.0` (`avr` / `at90usb`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`, `usbmsc`.
