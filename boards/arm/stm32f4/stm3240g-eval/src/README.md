# `stm3240g-eval/src` Component (`boards/arm/stm32f4/stm3240g-eval/src`)

## Overview
Board-level C implementation (`src`) for `stm3240g-eval` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 18 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm3240g-eval.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm3240g-eval.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm3240g-eval.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm3240g-eval.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[stm3240g-eval.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[stm3240g-eval.h:stm32_led_initialize]` Public declaration `stm32_led_initialize()`
- `[stm3240g-eval.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm3240g-eval.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm3240g-eval.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[stm3240g-eval.h:stm32_extmemgpios]` Public declaration `stm32_extmemgpios()`
- `[stm3240g-eval.h:stm32_extmemaddr]` Public declaration `stm32_extmemaddr()`
- `[stm3240g-eval.h:stm32_extmemdata]` Public declaration `stm32_extmemdata()`
- `[stm3240g-eval.h:stm32_selectsram]` Public declaration `stm32_selectsram()`
- `[stm3240g-eval.h:stm32_deselectsram]` Public declaration `stm32_deselectsram()`
- `[stm3240g-eval.h:stm32_selectlcd]` Public declaration `stm32_selectlcd()`
- `[stm3240g-eval.h:stm32_deselectlcd]` Public declaration `stm32_deselectlcd()`
- `[stm3240g-eval.h:HAVE_I2CTOOL]` Hardware/board configuration macros (`HAVE_I2CTOOL`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `MIN_IRQBUTTON` (+12 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:stm32_led_initialize]` Public function `stm32_led_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- *(+33 additional symbols across 18 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_STMPE811`, `CONFIG_PWM` (+3 more)
- `[stm3240g-eval.h:stm32_bringup]` Validates preconditions and returns `-EVAL` on failure
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_bringup.c:#error]` Compile-time guard: `Only one MMC/SD slot`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_extmem.c:#error]` Compile-time guard: `Required GPIO ports not enabled`
- `[stm32_lcd.c:DEBUGASSERT]` Requires `buffer && ((uintptr_t)buffer & 1) == 0`
- `[stm32_lcd.c:DEBUGASSERT]` Requires `dev && vinfo`
- `[stm32_lcd.c:#error]` Compile-time guard: `CONFIG_LCD_MAXPOWER must be less than 256 to fit in uint8_t`
- `[stm32_lcd.c:#error]` Compile-time guard: `Cannot define both portrait and any other orientations`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:stm32_led_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`stm32_led_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `i2c_register()`, `m25p_initialize()`, `nx_mount()`, `rtc_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_deselectlcd.c:stm32_deselectlcd]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_deselectsram.c:stm32_deselectsram]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_extmem.c:stm32_extmemgpios]` Configures or drives hardware GPIO pins
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_selectlcd.c:stm32_selectlcd]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh stm3240g-eval:nsh && make`
