# `eic7700-evb/src` Component (`boards/risc-v/eic7700x/eic7700-evb/src`)

## Overview
Board-level C implementation (`src`) for `eic7700-evb` (`risc-v/eic7700x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[board_config.h:eic7700x_bringup]` Public declaration `eic7700x_bringup()`
- `[eic7700x_bringup.c:eic7700x_bringup]` Public function `eic7700x_bringup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh eic7700-evb:nsh && make`
