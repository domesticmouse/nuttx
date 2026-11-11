# `tiva` Family Boards (`boards/arm/tiva`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `tiva` SoC/MCU family under the `arm` architecture (12 subdirectories).

## Subdirectories & Boundaries
- [`dk-tm4c129x`](./dk-tm4c129x/README.md) - Board Support Package (BSP) blueprint for `dk-tm4c129x` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `ipv6`, `nsh`.
- [`eagle100`](./eagle100/README.md) - Board Support Package (BSP) blueprint for `eagle100` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `httpd`, `nettest`, `nsh`, `nxflat`, `thttpd`.
- [`ekk-lm3s9b96`](./ekk-lm3s9b96/README.md) - Board Support Package (BSP) blueprint for `ekk-lm3s9b96` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`launchxl-cc1310`](./launchxl-cc1310/README.md) - Board Support Package (BSP) blueprint for `launchxl-cc1310` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`launchxl-cc1312r1`](./launchxl-cc1312r1/README.md) - Board Support Package (BSP) blueprint for `launchxl-cc1312r1` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`lm3s6432-s2e`](./lm3s6432-s2e/README.md) - Board Support Package (BSP) blueprint for `lm3s6432-s2e` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`lm3s6965-ek`](./lm3s6965-ek/README.md) - Board Support Package (BSP) blueprint for `lm3s6965-ek` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, kernel, src, tools`. Includes build configurations: `discover`, `nsh`, `nx`, `qemu-flat`, `qemu-kostest`, `qemu-nxflat` (+2 more).
- [`lm3s8962-ek`](./lm3s8962-ek/README.md) - Board Support Package (BSP) blueprint for `lm3s8962-ek` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nx`.
- [`lm4f120-launchpad`](./lm4f120-launchpad/README.md) - Board Support Package (BSP) blueprint for `lm4f120-launchpad` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`.
- [`tm4c123g-launchpad`](./tm4c123g-launchpad/README.md) - Board Support Package (BSP) blueprint for `tm4c123g-launchpad` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `mcp2515`, `nsh`.
- [`tm4c1294-launchpad`](./tm4c1294-launchpad/README.md) - Board Support Package (BSP) blueprint for `tm4c1294-launchpad` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `ipv6`, `nsh`.
- [`tm4c129e-launchpad`](./tm4c129e-launchpad/README.md) - Board Support Package (BSP) blueprint for `tm4c129e-launchpad` (`arm` / `tiva`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `ipv6`, `nsh`, `ostest`.
