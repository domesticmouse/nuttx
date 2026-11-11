# `skp16c26/src` Component (`boards/renesas/m16c/skp16c26/src`)

## Overview
Board-level C implementation (`src`) for `skp16c26` (`renesas/m16c`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[skp16c26.h]` Board header declarations `skp16c26.h`
- `[m16c_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[m16c_buttons.c:board_buttons]` Public function `board_buttons()`
- `[m16c_lcd.c:up_lcdwrite]` Public function `up_lcdwrite()`
- `[m16c_lcd.c:up_lcdinit]` Public function `up_lcdinit()`
- `[m16c_lcd.c:up_lcdputc]` Public function `up_lcdputc()`
- `[m16c_lcdconsole.c:up_earlyconsoleinit]` Public function `up_earlyconsoleinit()`
- `[m16c_lcdconsole.c:up_consoleinit]` Public function `up_consoleinit()`
- `[m16c_lcdconsole.c:renesas_lowputc]` Public function `renesas_lowputc()`
- `[m16c_lcdconsole.c:up_putc]` Public function `up_putc()`
- `[m16c_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[m16c_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[m16c_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- None

## Side Effects
- `[m16c_buttons.c:board_button_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[m16c_lcd.c:up_lcdwrite]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[m16c_leds.c:board_autoled_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh skp16c26:ostest && make`
