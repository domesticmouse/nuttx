# `nucleo-f334r8/src` Component (`boards/arm/stm32f3/nucleo-f334r8/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-f334r8` (`arm/stm32f3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-f334r8.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-f334r8.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[nucleo-f334r8.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-f334r8.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[nucleo-f334r8.h:stm32_comp_setup]` Public declaration `stm32_comp_setup()`
- `[nucleo-f334r8.h:stm32_opamp_setup]` Public declaration `stm32_opamp_setup()`
- `[nucleo-f334r8.h:stm32_hrtim_setup]` Public declaration `stm32_hrtim_setup()`
- `[nucleo-f334r8.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER` (+1 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_comp.c:stm32_comp_setup]` Public function `stm32_comp_setup()`
- `[stm32_highpri.c:adc12_handler]` Public function `adc12_handler()`
- `[stm32_highpri.c:dma1ch1_handler]` Public function `dma1ch1_handler()`
- `[stm32_highpri.c:highpri_main]` Public function `highpri_main()`
- `[stm32_hrtim.c:stm32_hrtim_setup]` Public function `stm32_hrtim_setup()`
- `[stm32_opamp.c:stm32_opamp_setup]` Public function `stm32_opamp_setup()`
- `[stm32_spwm.c:spwm_main]` Public function `spwm_main()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_COMP`, `CONFIG_NUCLEOF334R8_HIGHPRI`, `CONFIG_NUCLEOF334R8_SPWM` (+2 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_comp.c:#error]` Compile-time guard: `Currently only one COMP device supported`
- `[stm32_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_HIPRI_INTERRUPT is required`
- `[stm32_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_RAMVECTORS is required`
- `[stm32_hrtim.c:stm32_hrtim_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_opamp.c:stm32_opamp_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spwm.c:DEBUGASSERT]` Requires `x >= 0 && x <= 2 * M_PI`
- `[stm32_spwm.c:DEBUGASSERT]` Requires `spwm->waveform[i] >= 0.0 && spwm->waveform[i] <= 2 * M_PI`
- `[stm32_spwm.c:#error]` Compile-time guard: `CONFIG_ARCH_HIPRI_INTERRUPT is required`
- `[stm32_spwm.c:#error]` Compile-time guard: `CONFIG_ARCH_RAMVECTORS is required`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_common_initialize()`, `userled_lower_initialize()`)
- `[stm32_comp.c:stm32_comp_setup]` Initializes/registers kernel devices or filesystems (`comp_register()`)
- `[stm32_highpri.c:adc12_handler]` Configures or drives hardware GPIO pins
- `[stm32_highpri.c:adc12_handler]` Modifies interrupt controller or critical-section state
- `[stm32_hrtim.c:stm32_hrtim_setup]` Initializes/registers kernel devices or filesystems (`hrtim_register()`)
- `[stm32_opamp.c:stm32_opamp_setup]` Initializes/registers kernel devices or filesystems (`opamp_register()`)
- `[stm32_spwm.c:spwm_main]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh nucleo-f334r8:nsh && make`
