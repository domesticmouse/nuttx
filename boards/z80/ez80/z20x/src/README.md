# `z20x/src` Component (`boards/z80/ez80/z20x/src`)

## Overview
Board-level C implementation (`src`) for `z20x` (`z80/ez80`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[z20x.h:ez80_bringup]` Public declaration `ez80_bringup()`
- `[z20x.h:ez80_mmcsd_initialize]` Public declaration `ez80_mmcsd_initialize()`
- `[z20x.h:ez80_spidev_initialize]` Public declaration `ez80_spidev_initialize()`
- `[z20x.h:ez80_w25_initialize]` Public declaration `ez80_w25_initialize()`
- `[z20x.h:HAVE_SPIFLASH]` Hardware/board configuration macros (`HAVE_SPIFLASH`, `HAVE_MMCSD`, `HAVE_XPT2046`, `VECSTART`, `VECEND`, `VECSIZE` (+16 more))
- `[ez80_boot.c:ez80_board_initialize]` Public function `ez80_board_initialize()`
- `[ez80_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[ez80_bringup.c:ez80_bringup]` Public function `ez80_bringup()`
- `[ez80_spi.c:ez80_spidev_initialize]` Public function `ez80_spidev_initialize()`
- `[ez80_spi.c:ez80_spiselect]` Public function `ez80_spiselect()`
- `[ez80_spi.c:ez80_spistatus]` Public function `ez80_spistatus()`
- `[ez80_spi.c:ez80_spicmddata]` Public function `ez80_spicmddata()`
- `[ez80_spimmcsd.c:ez80_mmcsd_initialize]` Public function `ez80_mmcsd_initialize()`
- `[ez80_w25.c:ez80_w25_initialize]` Public function `ez80_w25_initialize()`
- `[sd_main.c:void]` Public function `void()`
- `[sd_main.c:sd_main]` Public function `sd_main()`
- `[w25_main.c:void]` Public function `void()`
- `[w25_main.c:w25_main]` Public function `w25_main()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_EZ80_SPI`, `CONFIG_MMCSD_SPI`, `CONFIG_MTD_W25`, `CONFIG_Z20X_SDBOOT`, `CONFIG_Z20X_W25BOOT`
- `[ez80_spi.c:ez80_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[ez80_spimmcsd.c:ez80_mmcsd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[ez80_w25.c:ez80_w25_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[w25_main.c:#error]` Compile-time guard: `The W25 Serial FLASH is not available`
- `[w25_main.c:#error]` Compile-time guard: `CONFIG_Z20X_W25_CHARDEV must be selected`

## Side Effects
- `[ez80_boot.c:ez80_board_initialize]` Initializes/registers kernel devices or filesystems (`ez80_spidev_initialize()`)
- `[ez80_bringup.c:ez80_bringup]` Initializes/registers kernel devices or filesystems (`ez80_mmcsd_initialize()`, `ez80_w25_initialize()`, `nx_mount()`)
- `[ez80_spimmcsd.c:ez80_mmcsd_initialize]` Initializes/registers kernel devices or filesystems (`ez80_spibus_initialize()`)
- `[ez80_w25.c:ez80_w25_initialize]` Initializes/registers kernel devices or filesystems (`ez80_spibus_initialize()`, `w25_initialize()`)

## Verification
- Run: `./tools/configure.sh z20x:nsh && make`
