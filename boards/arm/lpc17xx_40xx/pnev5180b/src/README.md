# `pnev5180b/src` Component (`boards/arm/lpc17xx_40xx/pnev5180b/src`)

## Overview
Board-level C implementation (`src`) for `pnev5180b` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpc17_40_romfs.h:lpc17_40_romfs_initialize]` Public declaration `lpc17_40_romfs_initialize()`
- `[lpc17_40_romfs.h:ROMFS_SECTOR_SIZE]` Hardware/board configuration macros (`ROMFS_SECTOR_SIZE`)
- `[lpc17_40_symtab.h]` Board header declarations `lpc17_40_symtab.h`
- `[pnev5180b.h:pnev5180b_bringup]` Public declaration `pnev5180b_bringup()`
- `[pnev5180b.h:pnev5180b_autoled_initialize]` Public declaration `pnev5180b_autoled_initialize()`
- `[pnev5180b.h:pnev5180b_spidev_initialize]` Public declaration `pnev5180b_spidev_initialize()`
- `[pnev5180b.h:PNEV5180B_LED_BLUE]` Hardware/board configuration macros (`PNEV5180B_LED_BLUE`, `PNEV5180B_LED_GREEN`, `PNEV5180B_LED_ORANGE`, `PNEV5180B_LED_RED`)
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_bringup.c:pnev5180b_bringup]` Public function `pnev5180b_bringup()`
- `[lpc17_40_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[lpc17_40_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[lpc17_40_leds.c:pnev5180b_autoled_initialize]` Public function `pnev5180b_autoled_initialize()`
- `[lpc17_40_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_romfs.c:lpc17_40_romfs_initialize]` Public function `lpc17_40_romfs_initialize()`
- `[lpc17_40_spi.c:pnev5180b_spidev_initialize]` Public function `pnev5180b_spidev_initialize()`
- `[lpc17_40_spi.c:lpc17_40_spiselect]` Public function `lpc17_40_spiselect()`
- `[lpc17_40_spi.c:lpc17_40_spistatus]` Public function `lpc17_40_spistatus()`
- `[lpc17_40_symtab.c:lpc17_40_exports]` Module symbol `lpc17_40_exports`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_ELF`, `CONFIG_LPC17_40_ROMFS`, `CONFIG_LPC17_40_SPI`, `CONFIG_NXFLAT`, `CONFIG_USBDEV_COMPOSITE`
- `[lpc17_40_bringup.c:#error]` Compile-time guard: `Unrecognized board`
- `[lpc17_40_romfs.c:#error]` Compile-time guard: `CONFIG_LPC17_40_ROMFS must be defined`
- `[lpc17_40_romfs.c:#error]` Compile-time guard: `CONFIG_LPC17_40_ROMFS_IMAGEFILE must be defined`

## Side Effects
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`pnev5180b_autoled_initialize()`)
- `[lpc17_40_bringup.c:pnev5180b_bringup]` Initializes/registers kernel devices or filesystems (`cdcacm_initialize()`, `cdcecm_initialize()`, `elf_initialize()`, `lpc17_40_romfs_initialize()`, `nx_mount()`)
- `[lpc17_40_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[lpc17_40_leds.c:pnev5180b_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_romfs.c:lpc17_40_romfs_initialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `romdisk_register()`)

## Verification
- Run: `./tools/configure.sh pnev5180b:nsh && make`
