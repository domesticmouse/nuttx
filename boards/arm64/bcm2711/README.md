# `bcm2711` Family Boards (`boards/arm64/bcm2711`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `bcm2711` SoC/MCU family under the `arm64` architecture (1 subdirectories).

## Subdirectories & Boundaries
- [`raspberrypi-4b`](./raspberrypi-4b/README.md) - Board Support Package (BSP) blueprint for `raspberrypi-4b` (`arm64` / `bcm2711`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audio_tone`, `baromonitor`, `bmp280`, `cgol`, `coremark`, `fb` (+8 more).
