# `stm32f334-disco/src` Component (`boards/arm/stm32f3/stm32f334-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32f334-disco` (`arm/stm32f3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f334-disco.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f334-disco.h:stm32_timer_driver_setup]` Public declaration `stm32_timer_driver_setup()`
- `[stm32f334-disco.h:stm32_dac_setup]` Public declaration `stm32_dac_setup()`
- `[stm32f334-disco.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32f334-disco.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm32f334-disco.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[stm32f334-disco.h:stm32_comp_setup]` Public declaration `stm32_comp_setup()`
- `[stm32f334-disco.h:stm32_opamp_setup]` Public declaration `stm32_opamp_setup()`
- `[stm32f334-disco.h:stm32_powerled_setup]` Public declaration `stm32_powerled_setup()`
- `[stm32f334-disco.h:stm32_smps_setup]` Public declaration `stm32_smps_setup()`
- `[stm32f334-disco.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON` (+4 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_comp.c:stm32_comp_setup]` Public function `stm32_comp_setup()`
- `[stm32_hrtim.c:stm32_hrtim_setup]` Public function `stm32_hrtim_setup()`
- `[stm32_opamp.c:stm32_opamp_setup]` Public function `stm32_opamp_setup()`
- `[stm32_powerled.c:stm32_powerled_setup]` Public function `stm32_powerled_setup()`
- `[stm32_powerled.c:g_powerled_ops]` Exported global symbol `g_powerled_ops`
- `[stm32_powerled.c:g_powerled_dev]` Exported global symbol `g_powerled_dev`
- *(+3 additional symbols across 9 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_DRIVERS_POWERLED`, `CONFIG_DRIVERS_SMPS`
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_comp.c:#error]` Compile-time guard: `Currently only one COMP device supported`
- `[stm32_hrtim.c:stm32_hrtim_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_opamp.c:stm32_opamp_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_powerled.c:#error]` Compile-time guard: `Powerled example requires HRTIM1 support`
- `[stm32_powerled.c:#error]` Compile-time guard: `Powerled example requires DAC1 with DMA support`
- `[stm32_smps.c:#error]` Compile-time guard: `CONFIG_LIBDSP is required`
- `[stm32_smps.c:#error]` Compile-time guard: `CONFIG_ARCH_HIPRI_INTERRUPT is required`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `userled_lower_initialize()`)
- `[stm32_comp.c:stm32_comp_setup]` Initializes/registers kernel devices or filesystems (`comp_register()`)
- `[stm32_hrtim.c:stm32_hrtim_setup]` Initializes/registers kernel devices or filesystems (`hrtim_register()`)
- `[stm32_opamp.c:stm32_opamp_setup]` Initializes/registers kernel devices or filesystems (`opamp_register()`)
- `[stm32_powerled.c:stm32_powerled_setup]` Initializes/registers kernel devices or filesystems (`powerled_register()`)
- `[stm32_smps.c:stm32_smps_setup]` Configures or drives hardware GPIO pins
- `[stm32_smps.c:stm32_smps_setup]` Initializes/registers kernel devices or filesystems (`smps_register()`)
- `[stm32_smps.c:stm32_smps_setup]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh stm32f334-disco:nsh && make`
