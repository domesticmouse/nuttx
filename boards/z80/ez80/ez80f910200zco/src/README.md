# `ez80f910200zco/src` Component (`boards/z80/ez80/ez80f910200zco/src`)

## Overview
Board-level C implementation (`src`) for `ez80f910200zco` (`z80/ez80`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[ez80f910200zco.h:EZ80_OFFCHIPFLASH]` Hardware/board configuration macros (`EZ80_OFFCHIPFLASH`, `EZ80_LEDGPIOCNTRL`, `EZ80_PLTFMSRAM`, `EZ80_MODULESRAM`, `EZ80_LEDANODE`, `EZ80_GPIOCNTRL` (+31 more))
- `[ez80_boot.c:ez80_board_initialize]` Public function `ez80_board_initialize()`
- `[ez80_buttons.c:ez80_pbinterrupt]` Public function `ez80_pbinterrupt()`
- `[ez80_buttons.c:ez80_pb1interrupt]` Public function `ez80_pb1interrupt()`
- `[ez80_buttons.c:ez80_pb2interrupt]` Public function `ez80_pb2interrupt()`
- `[ez80_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[ez80_buttons.c:board_buttons]` Public function `board_buttons()`
- `[ez80_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[ez80_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[ez80_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[ez80_leds.c:up_timerhook]` Public function `up_timerhook()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`

## Side Effects
- `[ez80_buttons.c:ez80_pbinterrupt]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh ez80f910200zco:nsh && make`
