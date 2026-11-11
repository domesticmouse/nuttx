# `pimoroni-pico-plus-2-w/src` Component (`boards/arm/rp23xx/pimoroni-pico-plus-2-w/src`)

## Overview
Board-level C implementation (`src`) for `pimoroni-pico-plus-2-w` (`arm/rp23xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rp23xx_pico.h:rp23xx_bringup]` Public declaration `rp23xx_bringup()`
- `[rp23xx_pico.h:rp23xx_dev_gpio_init]` Public declaration `rp23xx_dev_gpio_init()`
- `[rp23xx_pico.h:GPIO_CYW43439_ON]` Hardware/board configuration macros (`GPIO_CYW43439_ON`, `GPIO_CYW43439_DATA`, `GPIO_CYW43439_CS`, `GPIO_CYW43439_CLOCK`, `GPIO_BTN_USER1`, `MIN_IRQBUTTON` (+2 more))
- `[rp23xx_boardinitialize.c:rp23xx_boardearlyinitialize]` Public function `rp23xx_boardearlyinitialize()`
- `[rp23xx_boardinitialize.c:rp23xx_boardinitialize]` Public function `rp23xx_boardinitialize()`
- `[rp23xx_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rp23xx_bringup.c:rp23xx_bringup]` Public function `rp23xx_bringup()`
- `[rp23xx_bringup.c:g_cyw43439]` Exported global symbol `g_cyw43439`
- `[rp23xx_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[rp23xx_buttons.c:board_buttons]` Public function `board_buttons()`
- `[rp23xx_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[rp23xx_gpio.c:rp23xx_dev_gpio_init]` Public function `rp23xx_dev_gpio_init()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`, `CONFIG_USERLED`
- `[rp23xx_buttons.c:#error]` Compile-time guard: `The NuttX Buttons Driver depends on IRQ support to work!\n`
- `[rp23xx_gpio.c:DEBUGASSERT]` Requires `rp23xxgpio != NULL && value != NULL`
- `[rp23xx_gpio.c:DEBUGASSERT]` Requires `rp23xxgpio->id < BOARD_NGPIOOUT`
- `[rp23xx_gpio.c:DEBUGASSERT]` Requires `rp23xxgpio != NULL`

## Side Effects
- `[rp23xx_boardinitialize.c:rp23xx_boardearlyinitialize]` Initializes/registers kernel devices or filesystems (`rp23xx_common_initialize()`)
- `[rp23xx_bringup.c:rp23xx_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `userled_lower_initialize()`)
- `[rp23xx_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[rp23xx_gpio.c:rp23xx_dev_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh pimoroni-pico-plus-2-w:nsh && make`
