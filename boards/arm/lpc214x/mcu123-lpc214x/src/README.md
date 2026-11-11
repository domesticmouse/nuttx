# `mcu123-lpc214x/src` Component (`boards/arm/lpc214x/mcu123-lpc214x/src`)

## Overview
Board-level C implementation (`src`) for `mcu123-lpc214x` (`arm/lpc214x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[lpc2148_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc2148_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[lpc2148_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[lpc2148_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc2148_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc2148_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc2148_spi1.c:lpc214x_spibus_initialize]` Public function `lpc214x_spibus_initialize()`
- `[lpc2148_usbmsc.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_USBDEV_COMPOSITE`, `CONFIG_USBMSC`
- `[lpc2148_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[lpc2148_composite.c:DEBUGASSERT]` Requires `g_mschandle != NULL`
- `[lpc2148_spi1.c:#error]` Compile-time guard: `spi_cmddata not implemented`
- `[lpc2148_usbmsc.c:#error]` Compile-time guard: `Unrecognized LPC214x board`

## Side Effects
- `[lpc2148_boardinit.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`lpc214x_spibus_initialize()`)
- `[lpc2148_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`, `lpc214x_spibus_initialize()`)
- `[lpc2148_leds.c:board_autoled_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc2148_spi1.c:lpc214x_spibus_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc2148_usbmsc.c:board_usbmsc_initialize]` Initializes/registers kernel devices or filesystems (`lpc214x_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh mcu123-lpc214x:nsh && make`
