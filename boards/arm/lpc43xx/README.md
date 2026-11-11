# `lpc43xx` Family Boards (`boards/arm/lpc43xx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `lpc43xx` SoC/MCU family under the `arm` architecture (5 subdirectories).

## Subdirectories & Boundaries
- [`bambino-200e`](./bambino-200e/README.md) - Board Support Package (BSP) blueprint for `bambino-200e` (`arm` / `lpc43xx`). Coordinates board initialization, headers, and tooling across `include, kernel, scripts, src`. Includes build configurations: `knsh`, `max31855`, `netnsh`, `nsh`, `usbnsh`.
- [`lpc4330-xplorer`](./lpc4330-xplorer/README.md) - Board Support Package (BSP) blueprint for `lpc4330-xplorer` (`arm` / `lpc43xx`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `nsh`.
- [`lpc4337-ws`](./lpc4337-ws/README.md) - Board Support Package (BSP) blueprint for `lpc4337-ws` (`arm` / `lpc43xx`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `nsh`.
- [`lpc4357-evb`](./lpc4357-evb/README.md) - Board Support Package (BSP) blueprint for `lpc4357-evb` (`arm` / `lpc43xx`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `nsh`.
- [`lpc4370-link2`](./lpc4370-link2/README.md) - Board Support Package (BSP) blueprint for `lpc4370-link2` (`arm` / `lpc43xx`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `nsh`.
