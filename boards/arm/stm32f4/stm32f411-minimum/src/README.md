# `stm32f411-minimum/src` Component (`boards/arm/stm32f4/stm32f411-minimum/src`)

## Overview
Board-level C implementation (`src`) for `stm32f411-minimum` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f411-minimum-gpio.h:GPIO_A0_USED_OUT]` Hardware/board configuration macros (`GPIO_A0_USED_OUT`, `GPIO_A0_USED_INT`, `GPIO_A0_USED_IN`, `GPIO_A0_OUTTYPE`, `GPIO_A0_OUT_DEFAULT`, `GPIO_A0_PULL` (+317 more))
- `[stm32f411-minimum.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f411-minimum.h:stm32_hx711_initialize]` Public declaration `stm32_hx711_initialize()`
- `[stm32f411-minimum.h:stm32_mmcsd_initialize]` Public declaration `stm32_mmcsd_initialize()`
- `[stm32f411-minimum.h:stm32_w25initialize]` Public declaration `stm32_w25initialize()`
- `[stm32f411-minimum.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32f411-minimum.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[stm32f411-minimum.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[stm32f411-minimum.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32f411-minimum.h:stm32_rgbled_setup]` Public declaration `stm32_rgbled_setup()`
- `[stm32f411-minimum.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f411-minimum.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER`, `GPIO_BTN_EXTERNAL` (+8 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[stm32_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- *(+21 additional symbols across 16 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC_HX711`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_MTD_W25`, `CONFIG_PWM` (+7 more)
- `[stm32f411-minimum-gpio.h:#error]` Compile-time guard: `You have enabled more interrupts than supported, adjust CONFIG_DEV_GPIO_...`
- `[stm32_buttons.c:#error]` Compile-time guard: `The NuttX Buttons Driver depends on IRQ support to work!\n`
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < BOARD_NGPIO_IN`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_rgbled.c:#error]` Compile-time guard: `HAVE_RGBLED is undefined`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`
- `[stm32_w25.c:stm32_w25initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `stm32_gpio_initialize()`, `stm32_hx711_initialize()`, `stm32_usbhost_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_hx711.c:stm32_hx711_initialize]` Configures or drives hardware GPIO pins
- `[stm32_hx711.c:stm32_hx711_initialize]` Initializes/registers kernel devices or filesystems (`hx711_register()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_rgbled.c:stm32_rgbled_setup]` Initializes/registers kernel devices or filesystems (`rgbled_register()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32f411-minimum:nsh && make`
