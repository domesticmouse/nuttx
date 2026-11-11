# `w5500-evb-pico/src` Component (`boards/arm/rp2040/w5500-evb-pico/src`)

## Overview
Board-level C implementation (`src`) for `w5500-evb-pico` (`arm/rp2040`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rp2040_pico.h:rp2040_bringup]` Public declaration `rp2040_bringup()`
- `[rp2040_pico.h:rp2040_dev_gpio_init]` Public declaration `rp2040_dev_gpio_init()`
- `[rp2040_pico.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_BTN_USER1`, `GPIO_BTN_USER2`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`)
- `[rp2040_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[rp2040_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[rp2040_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[rp2040_boardinitialize.c:rp2040_boardearlyinitialize]` Public function `rp2040_boardearlyinitialize()`
- `[rp2040_boardinitialize.c:rp2040_boardinitialize]` Public function `rp2040_boardinitialize()`
- `[rp2040_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rp2040_bringup.c:rp2040_bringup]` Public function `rp2040_bringup()`
- `[rp2040_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[rp2040_buttons.c:board_buttons]` Public function `board_buttons()`
- `[rp2040_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[rp2040_gpio.c:rp2040_dev_gpio_init]` Public function `rp2040_dev_gpio_init()`
- `[rp2040_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[rp2040_userleds.c:board_userled]` Public function `board_userled()`
- `[rp2040_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[rp2040_userleds.c:rp2040_led_pminitialize]` Public function `rp2040_led_pminitialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`
- `[rp2040_buttons.c:#error]` Compile-time guard: `The NuttX Buttons Driver depends on IRQ support to work!\n`
- `[rp2040_gpio.c:DEBUGASSERT]` Requires `rp2040gpio != NULL && value != NULL`
- `[rp2040_gpio.c:DEBUGASSERT]` Requires `rp2040gpio->id < BOARD_NGPIOOUT`
- `[rp2040_gpio.c:DEBUGASSERT]` Requires `rp2040gpio != NULL`

## Side Effects
- `[rp2040_boardinitialize.c:rp2040_boardearlyinitialize]` Initializes/registers kernel devices or filesystems (`rp2040_common_initialize()`)
- `[rp2040_bringup.c:rp2040_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `userled_lower_initialize()`)
- `[rp2040_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[rp2040_gpio.c:rp2040_dev_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[rp2040_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh w5500-evb-pico:usbnsh && make`
