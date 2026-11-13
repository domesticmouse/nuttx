# `stm32g4` Family Boards (`boards/arm/stm32g4`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `stm32g4` SoC/MCU family under the `arm` architecture (6 subdirectories).

## Subdirectories & Boundaries
- [`b-g431b-esc1`](./b-g431b-esc1/README.md) - Board Support Package (BSP) blueprint for `b-g431b-esc1` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `cansock`, `foc_b16`, `foc_f32`, `nsh`.
- [`b-g474e-dpow1`](./b-g474e-dpow1/README.md) - Board Support Package (BSP) blueprint for `b-g474e-dpow1` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `buckboost`, `nsh`, `ostest`.
- [`nucleo-g431kb`](./nucleo-g431kb/README.md) - Board Support Package (BSP) blueprint for `nucleo-g431kb` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `comp`, `nsh`, `pwm`.
- [`nucleo-g431rb`](./nucleo-g431rb/README.md) - Board Support Package (BSP) blueprint for `nucleo-g431rb` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `can`, `cansock`, `cordic`, `ihm16m1_b16`, `ihm16m1_f32` (+3 more).
- [`nucleo-g474re`](./nucleo-g474re/README.md) - Board Support Package (BSP) blueprint for `nucleo-g474re` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `lpuartnsh`, `nsh`, `usbserial`.
- [`nucleo-g491re`](./nucleo-g491re/README.md) - Board Support Package (BSP) blueprint for `nucleo-g491re` (`arm` / `stm32g4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
