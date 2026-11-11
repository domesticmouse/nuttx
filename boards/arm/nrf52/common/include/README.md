# `common/include` Component (`boards/arm/nrf52/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s).

## Interface
- `[nrf52_ieee802154.h:nrf52_ieee802154_initialize]` Public declaration `nrf52_ieee802154_initialize()`
- `[nrf52_lsm9ds1.h:nrf52_lsm9ds1_initialize]` Public declaration `nrf52_lsm9ds1_initialize()`
- `[nrf52_mrf24j40.h:nrf52_mrf24j40_devsetup]` Public declaration `nrf52_mrf24j40_devsetup()`
- `[nrf52_mrf24j40.h:nrf52_mrf24j40_s]` Type definition `nrf52_mrf24j40_s`
- `[nrf52_progmem.h:nrf52_progmem_init]` Public declaration `nrf52_progmem_init()`
- `[nrf52_timer.h:nrf52_timer_driver_setup]` Public declaration `nrf52_timer_driver_setup()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
