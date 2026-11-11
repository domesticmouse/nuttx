# `rtl8730e_evb` Board Support Package (`boards/arm/rtl8730e/rtl8730e_evb`)

## Overview
Board Support Package (BSP) blueprint for `rtl8730e_evb` (`arm` / `rtl8730e`). Coordinates board initialization, headers, and tooling across `include, prebuilt, src`. Includes build configurations: `adc`, `gpio`, `i2c`, `nsh`, `pwm`, `rtc` (+4 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `rtl8730e_evb` (`arm/rtl8730e`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`prebuilt`](./prebuilt/README.md) - Board support component `prebuilt` for `rtl8730e_evb` (`arm/rtl8730e`), containing 1 source/script file(s) (`platform_autoconf.h`). Key symbols: `[platform_autoconf.h:CONFIG_AMEBASMART]` Hardware/board configuration macros (`CONFIG_AMEBASMART`, `CONFIG_ARM_CORE_CA32`, `CONFIG_FLASH_VFS1_OFFSET`, `CONFIG_FLASH_VFS1_SIZE`, `CONFIG_WHC_WIFI_API_PATH`, `CONFIG_WHC_HOST` (+3 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `rtl8730e_evb` (`arm/rtl8730e`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
