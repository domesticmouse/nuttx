# `nucleo-f722ze/src` Component (`boards/arm/stm32f7/nucleo-f722ze/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-f722ze` (`arm/stm32f7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-f722ze.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-f722ze.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-f722ze.h:stm32_dma_alloc_init]` Public declaration `stm32_dma_alloc_init()`
- `[nucleo-f722ze.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[nucleo-f722ze.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[nucleo-f722ze.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-f722ze.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-f722ze.h:stm32_bbsram_int]` Public declaration `stm32_bbsram_int()`
- `[nucleo-f722ze.h:stm32_qencoder_initialize]` Public declaration `stm32_qencoder_initialize()`
- `[nucleo-f722ze.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[nucleo-f722ze.h:GPIO_LD1]` Hardware/board configuration macros (`GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `GPIO_LED_GREEN`, `GPIO_LED_BLUE`, `GPIO_LED_RED` (+38 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_bbsram.c:stm32_bbsram_int]` Public function `stm32_bbsram_int()`
- `[stm32_bbsram.c:board_crashdump]` Public function `board_crashdump()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_bringup.c:board_timerhook]` Public function `board_timerhook()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- *(+34 additional symbols across 15 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`, `CONFIG_MMCSD` (+6 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_bbsram.c:stm32_bbsram_int]` Validates preconditions and returns `-ENOSPC`, `-ENXIO` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[stm32_composite.c:DEBUGASSERT]` Requires `epin < STM32_NENDPOINTS`
- `[stm32_composite.c:DEBUGASSERT]` Requires `epout < STM32_NENDPOINTS`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpint != NULL && stm32gpint->callback != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < BOARD_NGPIOIN`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_sdio.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_adc_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_bbsram.c:stm32_bbsram_int]` Modifies interrupt controller or critical-section state
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`mpu60x0_register()`, `stm32_common_initialize()`, `stm32_gpio_initialize()`, `stm32_i2cbus_initialize()`, `stm32_qencoder_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_sdio.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-f722ze:nsh && make`
