# `zp214xpa/src` Component (`boards/arm/lpc214x/zp214xpa/src`)

## Overview
Board-level C implementation (`src`) for `zp214xpa` (`arm/lpc214x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[lpc2148_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc2148_spi1.c:lpc214x_spibus_initialize]` Public function `lpc214x_spibus_initialize()`
- `[lpc2148_ug2864ambag01.c:board_graphics_setup]` Public function `board_graphics_setup()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_LCD_UG2864AMBAG01`
- `[lpc2148_ug2864ambag01.c:#error]` Compile-time guard: `The OLED driver requires CONFIG_SPI_CMDDATA in the configuration`

## Side Effects
- `[lpc2148_boardinit.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`fb_register()`, `nx_mount()`)
- `[lpc2148_spi1.c:lpc214x_spibus_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc2148_ug2864ambag01.c:board_graphics_setup]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc2148_ug2864ambag01.c:board_graphics_setup]` Initializes/registers kernel devices or filesystems (`lpc214x_spibus_initialize()`, `ug2864ambag01_initialize()`)

## Verification
- Run: `./tools/configure.sh zp214xpa:nsh && make`
