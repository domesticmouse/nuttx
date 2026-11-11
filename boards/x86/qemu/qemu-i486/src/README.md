# `qemu-i486/src` Component (`boards/x86/qemu/qemu-i486/src`)

## Overview
Board-level C implementation (`src`) for `qemu-i486` (`x86/qemu`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[qemu_i486.h:qemu_bringup]` Public declaration `qemu_bringup()`
- `[qemu_boot.c:x86_boardinitialize]` Public function `x86_boardinitialize()`
- `[qemu_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[qemu_bringup.c:qemu_bringup]` Public function `qemu_bringup()`
- `[qemu_vga_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[qemu_vga_lcd.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[qemu_vga_lcd.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ETC_ROMFS`, `CONFIG_QEMU_VGA`, `CONFIG_SYSTEM_NXINIT`

## Side Effects
- `[qemu_boot.c:x86_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[qemu_bringup.c:qemu_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `nx_mount()`)
- `[qemu_vga_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`qemu_vga_initialize()`)

## Verification
- Run: `./tools/configure.sh qemu-i486:nsh && make`
