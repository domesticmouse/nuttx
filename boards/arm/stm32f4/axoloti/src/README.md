# `axoloti/src` Component (`boards/arm/stm32f4/axoloti/src`)

## Overview
Board-level C implementation (`src`) for `axoloti` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[axoloti.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[axoloti.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[axoloti.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[axoloti.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[axoloti.h:stm32_adau1961_initialize]` Public declaration `stm32_adau1961_initialize()`
- `[axoloti.h:stm32_sdram_initialize]` Public declaration `stm32_sdram_initialize()`
- `[axoloti.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBHOST`, `HAVE_SDIO`, `HAVE_ADAU1961`, `HAVE_SDRAM`, `ADAU1961_I2C_BUS` (+14 more))
- `[stm32_adau1961.c:stm32_adau1961_initialize]` Public function `stm32_adau1961_initialize()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_extmem.c:stm32_sdram_memtest]` Public function `stm32_sdram_memtest()`
- `[stm32_extmem.c:stm32_sdram_initialize]` Public function `stm32_sdram_initialize()`
- `[stm32_sdio.c:stm32_sdio_initialize]` Public function `stm32_sdio_initialize()`
- `[stm32_usbhost.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- `[stm32_usbhost.c:stm32_usbhost_vbusdrive]` Public function `stm32_usbhost_vbusdrive()`
- `[stm32_usbhost.c:stm32_setup_overcurrent]` Public function `stm32_setup_overcurrent()`
- `[stm32_usbhost.c:stm32_usbhost_initialize]` Public function `stm32_usbhost_initialize()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- *(+1 additional symbols across 9 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_ADAU1961`, `CONFIG_STM32_FMC`, `CONFIG_STM32_SDIO` (+1 more)
- `[stm32_adau1961.c:DEBUGASSERT]` Requires `minor >= 0 && minor <= 25`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_sdio.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usbhost.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_adau1961.c:stm32_adau1961_initialize]` Configures or drives hardware GPIO pins
- `[stm32_adau1961.c:stm32_adau1961_initialize]` Initializes/registers kernel devices or filesystems (`adau1961_initialize()`, `audio_register()`, `stm32_i2cbus_initialize()`, `stm32_sai_initialize()`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `rei2c_initialize()`, `stm32_adau1961_initialize()`, `stm32_sdio_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_extmem.c:stm32_sdram_memtest]` Configures or drives hardware GPIO pins
- `[stm32_sdio.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdio.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_usbhost.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usbhost.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_otghshost_initialize()`, `usbhost_msc_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh axoloti:nsh && make`
