# `n32h762iil7/src` Component (`boards/arm/n32h7/n32h762iil7/src`)

## Overview
Board-level C implementation (`src`) for `n32h762iil7` (`arm/n32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[n32h762iil7.h:n32_bringup]` Public declaration `n32_bringup()`
- `[n32h762iil7.h:n32_spidev_initialize]` Public declaration `n32_spidev_initialize()`
- `[n32h762iil7.h:n32_adc_setup]` Public declaration `n32_adc_setup()`
- `[n32h762iil7.h:n32_gpio_initialize]` Public declaration `n32_gpio_initialize()`
- `[n32h762iil7.h:n32_usbinitialize]` Public declaration `n32_usbinitialize()`
- `[n32h762iil7.h:n32_usbhost_initialize]` Public declaration `n32_usbhost_initialize()`
- `[n32h762iil7.h:n32_pwm_setup]` Public declaration `n32_pwm_setup()`
- `[n32h762iil7.h:n32_progmem_init]` Public declaration `n32_progmem_init()`
- `[n32h762iil7.h:n32_cordic_setup]` Public declaration `n32_cordic_setup()`
- `[n32h762iil7.h:n32_sdmmc_initialize]` Public declaration `n32_sdmmc_initialize()`
- `[n32h762iil7.h:HAVE_PROC]` Hardware/board configuration macros (`HAVE_PROC`, `HAVE_SDIO`, `HAVE_USBDEV`, `HAVE_USBHOST`, `HAVE_USBMONITOR`, `HAVE_MTDCONFIG` (+20 more))
- `[n32_appinitialize.c:board_app_initialize]` Public function `board_app_initialize()`
- `[n32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[n32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[n32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[n32_boot.c:n32_boardinitialize]` Public function `n32_boardinitialize()`
- `[n32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[n32_bringup.c:n32_timer_initialize]` Public function `n32_timer_initialize()`
- `[n32_bringup.c:n32_cap_initialize]` Public function `n32_cap_initialize()`
- `[n32_bringup.c:n32_bringup]` Public function `n32_bringup()`
- `[n32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[n32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[n32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- *(+18 additional symbols across 15 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARDCTL_UNIQUEID` (+6 more)
- `[n32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[n32_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[n32_composite.c:DEBUGASSERT]` Requires `epin < N32_USBHS_NENDPOINTS`
- `[n32_composite.c:DEBUGASSERT]` Requires `epout < N32_USBHS_NENDPOINTS`
- `[n32_cordic.c:n32_cordic_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[n32_progmem.c:n32_progmem_init]` Validates preconditions and returns `-EIO` on failure
- `[n32_pwm.c:n32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[n32_sdmmc.c:n32_sdmmc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[n32_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure
- `[n32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[n32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[n32_boot.c:n32_boardinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[n32_boot.c:n32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[n32_bringup.c:n32_timer_initialize]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `cap_register()`, `cdcacm_initialize()`, `n32_sdmmc_initialize()`, `n32_usbhost_initialize()`)
- `[n32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[n32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[n32_cordic.c:n32_cordic_setup]` Initializes/registers kernel devices or filesystems (`cordic_register()`)
- `[n32_progmem.c:n32_progmem_init]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `progmem_initialize()`)
- `[n32_pwm.c:n32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[n32_sdmmc.c:n32_sdmmc_initialize]` Configures or drives hardware GPIO pins
- `[n32_sdmmc.c:n32_sdmmc_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[n32_usb.c:n32_usbhshost_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh n32h762iil7:nsh && make`
