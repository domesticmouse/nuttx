# `common/include` Component (`boards/arm/nrf91/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`arm/nrf91`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s).

## Interface
- `[nrf91_adxl362.h:nrf91_adxl362_init]` Public declaration `nrf91_adxl362_init()`
- `[nrf91_adxl372.h:nrf91_adxl372_init]` Public declaration `nrf91_adxl372_init()`
- `[nrf91_bh1749nuc.h:nrf91_bh1749nuc_init]` Public declaration `nrf91_bh1749nuc_init()`
- `[nrf91_bme680.h:nrf91_bme680_init]` Public declaration `nrf91_bme680_init()`
- `[nrf91_progmem.h:nrf91_progmem_init]` Public declaration `nrf91_progmem_init()`
- `[nrf91_timer.h:nrf91_timer_driver_setup]` Public declaration `nrf91_timer_driver_setup()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
