# `common/include` Component (`boards/arm/nrf53/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`arm/nrf53`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 8 header file(s).

## Interface
- `[nrf53_adxl362.h:nrf53_adxl362_init]` Public declaration `nrf53_adxl362_init()`
- `[nrf53_bh1749nuc.h:nrf53_bh1749nuc_init]` Public declaration `nrf53_bh1749nuc_init()`
- `[nrf53_bme688.h:nrf53_bme688_init]` Public declaration `nrf53_bme688_init()`
- `[nrf53_bmi270.h:nrf53_bmi270spi_initialize]` Public declaration `nrf53_bmi270spi_initialize()`
- `[nrf53_bmi270.h:nrf53_bmi270i2c_initialize]` Public declaration `nrf53_bmi270i2c_initialize()`
- `[nrf53_bmm150.h:nrf53_bmm150_init]` Public declaration `nrf53_bmm150_init()`
- `[nrf53_ieee802154.h:nrf53_ieee802154_initialize]` Public declaration `nrf53_ieee802154_initialize()`
- `[nrf53_progmem.h:nrf53_progmem_init]` Public declaration `nrf53_progmem_init()`
- `[nrf53_timer.h:nrf53_timer_driver_setup]` Public declaration `nrf53_timer_driver_setup()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
