# `stm32f3` Family Boards (`boards/arm/stm32f3`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32f3` SoC/MCU family under the `arm` architecture (6 subdirectories).

## Subdirectories & Boundaries
- [`nucleo-f302r8`](./nucleo-f302r8/README.md) - Board Support Package (BSP) blueprint for `nucleo-f302r8` (`arm` / `stm32f3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `cansock`, `highpri`, `ihm07m1_b16`, `ihm07m1_f32`, `nsh` (+1 more).
- [`nucleo-f303re`](./nucleo-f303re/README.md) - Board Support Package (BSP) blueprint for `nucleo-f303re` (`arm` / `stm32f3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `can`, `hello`, `nsh`, `nxlines`, `pwm` (+1 more).
- [`nucleo-f303ze`](./nucleo-f303ze/README.md) - Board Support Package (BSP) blueprint for `nucleo-f303ze` (`arm` / `stm32f3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `nsh`, `nxlines_oled`.
- [`nucleo-f334r8`](./nucleo-f334r8/README.md) - Board Support Package (BSP) blueprint for `nucleo-f334r8` (`arm` / `stm32f3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `highpri`, `nsh`, `spwm1`, `spwm2`.
- [`stm32f334-disco`](./stm32f334-disco/README.md) - Board Support Package (BSP) blueprint for `stm32f334-disco` (`arm` / `stm32f3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `buckboost`, `nsh`, `powerled`.
- [`stm32f3discovery`](./stm32f3discovery/README.md) - Board Support Package (BSP) blueprint for `stm32f3discovery` (`arm` / `stm32f3`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`.
