# `makerlisp/src` Component (`boards/z80/ez80/makerlisp/src`)

## Overview
Board-level C implementation (`src`) for `makerlisp` (`z80/ez80`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[makerlisp.h:ez80_bringup]` Public declaration `ez80_bringup()`
- `[makerlisp.h:ez80_mmcsd_initialize]` Public declaration `ez80_mmcsd_initialize()`
- `[makerlisp.h:ez80_spidev_initialize]` Public declaration `ez80_spidev_initialize()`
- `[makerlisp.h:HAVE_MMCSD]` Hardware/board configuration macros (`HAVE_MMCSD`, `EZ80_GPIOD0`, `EZ80_GPIOD1`, `EZ80_GPIOD2`, `EZ80_GPIOD3`, `EZ80_GPIOD4` (+3 more))
- `[ez80_boot.c:ez80_board_initialize]` Public function `ez80_board_initialize()`
- `[ez80_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[ez80_boot.c:g_ebpresent]` Exported global symbol `g_ebpresent`
- `[ez80_bringup.c:ez80_bringup]` Public function `ez80_bringup()`
- `[ez80_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[ez80_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[ez80_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[ez80_spi.c:ez80_spidev_initialize]` Public function `ez80_spidev_initialize()`
- `[ez80_spi.c:ez80_spiselect]` Public function `ez80_spiselect()`
- `[ez80_spi.c:ez80_spistatus]` Public function `ez80_spistatus()`
- `[ez80_spi.c:ez80_spicmddata]` Public function `ez80_spicmddata()`
- `[ez80_spimmcsd.c:ez80_mmcsd_initialize]` Public function `ez80_mmcsd_initialize()`
- `[sd_main.c:void]` Public function `void()`
- `[sd_main.c:sd_main]` Public function `sd_main()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_EZ80_SPI`, `CONFIG_MAKERLISP_SDBOOT`, `CONFIG_MMCSD_SPI`
- `[ez80_spi.c:ez80_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[ez80_spimmcsd.c:ez80_mmcsd_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[ez80_boot.c:ez80_board_initialize]` Initializes/registers kernel devices or filesystems (`ez80_spidev_initialize()`, `ez80_vga_initialize()`)
- `[ez80_bringup.c:ez80_bringup]` Initializes/registers kernel devices or filesystems (`ez80_mmcsd_initialize()`, `nx_mount()`)
- `[ez80_spimmcsd.c:ez80_mmcsd_initialize]` Initializes/registers kernel devices or filesystems (`ez80_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh makerlisp:nsh_flash && make`
