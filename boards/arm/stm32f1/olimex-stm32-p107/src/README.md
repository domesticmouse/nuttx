# `olimex-stm32-p107/src` Component (`boards/arm/stm32f1/olimex-stm32-p107/src`)

## Overview
Board-level C implementation (`src`) for `olimex-stm32-p107` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[olimex-stm32-p107.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[olimex-stm32-p107.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[olimex-stm32-p107.h:GPIO_ENCX24J600_CS]` Hardware/board configuration macros (`GPIO_ENCX24J600_CS`, `GPIO_ENCX24J600_INTR`)
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_encx24j600.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- `[stm32_spi.c:stm32_spi3status]` Public function `stm32_spi3status()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ENCX24J600`, `CONFIG_STM32_CAN_CHARDRIVER`
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_encx24j600.c:DEBUGASSERT]` Requires `priv->handler != NULL`
- `[stm32_encx24j600.c:#error]` Compile-time guard: `Need CONFIG_STM32_SPI3 in the configuration`
- `[stm32_encx24j600.c:#error]` Compile-time guard: `SPI should be remapped for UEXT use`

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`stm32_spidev_initialize()`)
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_encx24j600.c:arm_netinitialize]` Initializes/registers kernel devices or filesystems (`enc_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh olimex-stm32-p107:nsh && make`
