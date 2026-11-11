# `lpc17xx_40xx` Family Boards (`boards/arm/lpc17xx_40xx`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `lpc17xx_40xx` SoC/MCU family under the `arm` architecture (12 subdirectories).

## Subdirectories & Boundaries
- [`lincoln60`](./lincoln60/README.md) - Board Support Package (BSP) blueprint for `lincoln60` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`, `thttpd-binfs`.
- [`lpc4088-devkit`](./lpc4088-devkit/README.md) - Board Support Package (BSP) blueprint for `lpc4088-devkit` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, kernel, src, tools`. Includes build configurations: `knsh`, `nsh`.
- [`lpc4088-quickstart`](./lpc4088-quickstart/README.md) - Board Support Package (BSP) blueprint for `lpc4088-quickstart` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, kernel, src, tools`. Includes build configurations: `knsh`, `nsh`.
- [`lpcxpresso-lpc1768`](./lpcxpresso-lpc1768/README.md) - Board Support Package (BSP) blueprint for `lpcxpresso-lpc1768` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `dhcpd`, `nsh`, `nx`, `thttpd`, `usbmsc`.
- [`lx_cpu`](./lx_cpu/README.md) - Board Support Package (BSP) blueprint for `lx_cpu` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`.
- [`mbed`](./mbed/README.md) - Board Support Package (BSP) blueprint for `mbed` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `userled`.
- [`mcb1700`](./mcb1700/README.md) - Board Support Package (BSP) blueprint for `mcb1700` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`olimex-lpc1766stk`](./olimex-lpc1766stk/README.md) - Board Support Package (BSP) blueprint for `olimex-lpc1766stk` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `ftpc`, `hidkbd`, `hidmouse`, `nettest`, `nsh`, `slip-httpd` (+5 more).
- [`open1788`](./open1788/README.md) - Board Support Package (BSP) blueprint for `open1788` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, kernel, src, tools`. Includes build configurations: `fb`, `knsh`, `knxterm`, `nsh`, `nxlines`, `pdcurses` (+1 more).
- [`pnev5180b`](./pnev5180b/README.md) - Board Support Package (BSP) blueprint for `pnev5180b` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `knsh`, `nsh`, `nsh-cdcecm`, `usbnsh`, `usbnsh-cdcecm`.
- [`u-blox-c027`](./u-blox-c027/README.md) - Board Support Package (BSP) blueprint for `u-blox-c027` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`.
- [`zkit-arm-1769`](./zkit-arm-1769/README.md) - Board Support Package (BSP) blueprint for `zkit-arm-1769` (`arm` / `lpc17xx_40xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`, `nxhello`, `thttpd`.
