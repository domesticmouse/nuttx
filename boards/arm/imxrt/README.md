# `imxrt` Family Boards (`boards/arm/imxrt`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `imxrt` SoC/MCU family under the `arm` architecture (10 subdirectories).

## Subdirectories & Boundaries
- [`arcx-socket-grid`](./arcx-socket-grid/README.md) - Board Support Package (BSP) blueprint for `arcx-socket-grid` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `nsh`, `usbdisk`.
- [`ddcnc-ec300`](./ddcnc-ec300/README.md) - Board Support Package (BSP) blueprint for `ddcnc-ec300` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`.
- [`fmu-v6xrt`](./fmu-v6xrt/README.md) - Board Support Package (BSP) blueprint for `fmu-v6xrt` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `rptun`.
- [`imxrt1020-evk`](./imxrt1020-evk/README.md) - Board Support Package (BSP) blueprint for `imxrt1020-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`, `usdhc`.
- [`imxrt1050-evk`](./imxrt1050-evk/README.md) - Board Support Package (BSP) blueprint for `imxrt1050-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `libcxxtest`, `netnsh`, `nsh`.
- [`imxrt1060-evk`](./imxrt1060-evk/README.md) - Board Support Package (BSP) blueprint for `imxrt1060-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `can`, `canfd`, `knsh`, `libcxxtest`, `lvgl`, `netnsh` (+3 more).
- [`imxrt1064-evk`](./imxrt1064-evk/README.md) - Board Support Package (BSP) blueprint for `imxrt1064-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `can`, `canfd`, `knsh`, `libcxxtest`, `lvgl`, `mcuboot-app` (+4 more).
- [`imxrt1170-evk`](./imxrt1170-evk/README.md) - Board Support Package (BSP) blueprint for `imxrt1170-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `can`, `canfd`, `knsh`, `libcxxtest`, `netnsh`, `nsh`.
- [`imxrt1180-evk`](./imxrt1180-evk/README.md) - Board Support Package (BSP) blueprint for `imxrt1180-evk` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `bl`, `nsh`, `nsh-m33`.
- [`teensy-4.x`](./teensy-4.x/README.md) - Board Support Package (BSP) blueprint for `teensy-4.x` (`arm` / `imxrt`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `can-4.1`, `enc-4.1`, `lcd-4.1`, `lua-4.1`, `netnsh-4.1`, `nsh-4.0` (+4 more).
