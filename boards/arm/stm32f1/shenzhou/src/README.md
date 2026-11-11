# `shenzhou/src` Component (`boards/arm/stm32f1/shenzhou/src`)

## Overview
Board-level C implementation (`src`) for `shenzhou` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[shenzhou.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[shenzhou.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[shenzhou.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[shenzhou.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[shenzhou.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[shenzhou.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[shenzhou.h:stm32_sdinitialize]` Public declaration `stm32_sdinitialize()`
- `[shenzhou.h:stm32_w25initialize]` Public declaration `stm32_w25initialize()`
- `[shenzhou.h:GPIO_MII_INT]` Hardware/board configuration macros (`GPIO_MII_INT`, `GPIO_WIRELESS_CS`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_WAKEUP` (+82 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_autoleds.c:up_ledpminitialize]` Public function `up_ledpminitialize()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_chipid.c:stm32_getchipid]` Public function `stm32_getchipid()`
- `[stm32_chipid.c:stm32_getchipid_string]` Public function `stm32_getchipid_string()`
- `[stm32_ili93xx.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- *(+34 additional symbols across 17 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_ARCH_RELAYS`, `CONFIG_INPUT_ADS7843E` (+5 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_boot.c:#error]` Compile-time guard: `Only one MMC/SD slot: Slot 0`
- `[stm32_boot.c:#error]` Compile-time guard: `Only one MMC/SD port: SPI1`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_ili93xx.c:DEBUGASSERT]` Requires `buffer && ((uintptr_t)buffer & 1) == 0`
- `[stm32_ili93xx.c:DEBUGASSERT]` Requires `dev && vinfo`
- `[stm32_ili93xx.c:#error]` Compile-time guard: `CONFIG_LCD_MAXPOWER must be less than 256 to fit in uint8_t`
- `[stm32_ili93xx.c:#error]` Compile-time guard: `Cannot define both portrait and any other orientations`
- `[stm32_mmcsd.c:stm32_sdinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_ssd1289.c:DEBUGASSERT]` Requires `lcddev == 0`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_autoleds.c:board_autoled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`, `stm32_usbhost_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_ili93xx.c:board_lcd_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_ili93xx.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[stm32_mmcsd.c:stm32_sdinitialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)
- `[stm32_relays.c:up_relaysinit]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh shenzhou:nsh && make`
