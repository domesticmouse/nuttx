# `nrf5340-dk/src` Component (`boards/arm/nrf53/nrf5340-dk/src`)

## Overview
Board-level C implementation (`src`) for `nrf5340-dk` (`arm/nrf53`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nrf5340-dk.h:nrf53_bringup]` Public declaration `nrf53_bringup()`
- `[nrf5340-dk.h:nrf53_pwm_setup]` Public declaration `nrf53_pwm_setup()`
- `[nrf5340-dk.h:nrf53_adc_setup]` Public declaration `nrf53_adc_setup()`
- `[nrf5340-dk.h:nrf53_mx25_initialize]` Public declaration `nrf53_mx25_initialize()`
- `[nrf5340-dk.h:nrf53_gpio_initialize]` Public declaration `nrf53_gpio_initialize()`
- `[nrf5340-dk.h:nrf53_qencoder_initialize]` Public declaration `nrf53_qencoder_initialize()`
- `[nrf5340-dk.h:NRF53_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`NRF53_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `GPIO_BUTTON1` (+14 more))
- `[nrf53_adc.c:nrf53_adc_setup]` Public function `nrf53_adc_setup()`
- `[nrf53_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[nrf53_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nrf53_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[nrf53_boot.c:nrf53_board_initialize]` Public function `nrf53_board_initialize()`
- `[nrf53_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nrf53_bringup.c:rpmsg_serialinit]` Public function `rpmsg_serialinit()`
- `[nrf53_bringup.c:nrf53_bringup]` Public function `nrf53_bringup()`
- `[nrf53_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[nrf53_buttons.c:board_buttons]` Public function `board_buttons()`
- `[nrf53_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[nrf53_composite.c:board_composite0_connect]` Public function `board_composite0_connect()`
- `[nrf53_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[nrf53_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[nrf53_cpunet_boot.c:nrf53_board_gpio_cpunet_allow]` Public function `nrf53_board_gpio_cpunet_allow()`
- `[nrf53_gpio.c:nrf53_gpio_initialize]` Public function `nrf53_gpio_initialize()`
- *(+7 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`, `CONFIG_NRF53_APPCORE` (+5 more)
- `[nrf53_adc.c:nrf53_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_bringup.c:#error]` Compile-time guard: `# endif`
- `[nrf53_composite.c:DEBUGASSERT]` Requires `epin <= NRF53_NENDPOINTS`
- `[nrf53_composite.c:DEBUGASSERT]` Requires `epout <= NRF53_NENDPOINTS`
- `[nrf53_gpio.c:DEBUGASSERT]` Requires `nrf53gpint != NULL && nrf53gpint->callback != NULL`
- `[nrf53_gpio.c:DEBUGASSERT]` Requires `nrf53gpio != NULL && value != NULL`
- `[nrf53_gpio.c:DEBUGASSERT]` Requires `nrf53gpio->id < BOARD_NGPIOIN`
- `[nrf53_pwm.c:nrf53_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[nrf53_qencoder.c:nrf53_qencoder_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[nrf53_adc.c:nrf53_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[nrf53_boot.c:nrf53_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[nrf53_bringup.c:rpmsg_serialinit]` Initializes/registers kernel devices or filesystems (`bt_driver_register()`, `btn_lower_initialize()`, `nrf53_gpio_initialize()`, `nrf53_ieee802154_initialize()`, `nrf53_mx25_initialize()`)
- `[nrf53_composite.c:board_composite0_connect]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[nrf53_gpio.c:nrf53_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[nrf53_mx25.c:nrf53_mx25_initialize]` Initializes/registers kernel devices or filesystems (`mx25rxx_initialize()`, `nrf53_qspi_initialize()`, `nx_mount()`)
- `[nrf53_pwm.c:nrf53_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[nrf53_qencoder.c:nrf53_qencoder_initialize]` Initializes/registers kernel devices or filesystems (`qe_register()`)

## Verification
- Run: `./tools/configure.sh nrf5340-dk:adc_cpuapp && make`
