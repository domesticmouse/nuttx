# `or1k/src` Component (`boards/or1k/mor1kx/or1k/src`)

## Overview
Board-level C implementation (`src`) for `or1k` (`or1k/mor1kx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[or1k.h:or1k_bringup]` Public declaration `or1k_bringup()`
- `[or1k_autoled.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[or1k_autoled.c:board_autoled_on]` Public function `board_autoled_on()`
- `[or1k_autoled.c:board_autoled_off]` Public function `board_autoled_off()`
- `[or1k_boot.c:or1k_board_initialize]` Public function `or1k_board_initialize()`
- `[or1k_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[or1k_bringup.c:or1k_bringup]` Public function `or1k_bringup()`

## Invariants
- None

## Side Effects
- `[or1k_boot.c:or1k_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[or1k_bringup.c:or1k_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)

## Verification
- Run: `./tools/configure.sh or1k:nsh && make`
