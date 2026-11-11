# `stm32f429i-disco/src` Component (`boards/arm/stm32f4/stm32f429i-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32f429i-disco` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f429i-disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f429i-disco.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f429i-disco.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32f429i-disco.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[stm32f429i-disco.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[stm32f429i-disco.h:stm32_sdram_initialize]` Public declaration `stm32_sdram_initialize()`
- `[stm32f429i-disco.h:stm32_ledpminitialize]` Public declaration `stm32_ledpminitialize()`
- `[stm32f429i-disco.h:stm32_pmbuttons]` Public declaration `stm32_pmbuttons()`
- `[stm32f429i-disco.h:stm32_ili93414ws_initialize]` Public declaration `stm32_ili93414ws_initialize()`
- `[stm32f429i-disco.h:stm32_spi5initialize]` Public declaration `stm32_spi5initialize()`
- `[stm32f429i-disco.h:stm32_l3gd20initialize]` Public declaration `stm32_l3gd20initialize()`
- `[stm32f429i-disco.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32f429i-disco.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm32f429i-disco.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[stm32f429i-disco.h:HAVE_PROC]` Hardware/board configuration macros (`HAVE_PROC`, `HAVE_USBDEV`, `HAVE_USBHOST`, `HAVE_USBMONITOR`, `STMPE811_ADDR1`, `STMPE811_ADDR2` (+17 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- *(+46 additional symbols across 17 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_IDLE_CUSTOM`, `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_STMPE811` (+9 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_extmem.c:#error]` Compile-time guard: `Required GPIO ports not enabled`
- `[stm32_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_HIPRI_INTERRUPT is required`
- `[stm32_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_RAMVECTORS is required`
- `[stm32_lcd.c:#error]` Compile-time guard: `display orientation not defined`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_stmpe811.c:DEBUGASSERT]` Requires `priv`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `ccm_initialize()`, `stm32_sdram_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_l3gd20_initialize()`, `btn_lower_initialize()`, `fb_register()`, `mtdconfig_register()`, `nx_mount()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_extmem.c:stm32_sdram_initialize]` Configures or drives hardware GPIO pins
- `[stm32_highpri.c:adc_handler]` Configures or drives hardware GPIO pins
- `[stm32_highpri.c:adc_handler]` Modifies interrupt controller or critical-section state
- `[stm32_idle.c:up_idle]` Modifies interrupt controller or critical-section state
- `[stm32_ili93414ws.c:stm32_ili93414ws_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh stm32f429i-disco:nsh && make`
