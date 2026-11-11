# `freedom-kl25z/src` Component (`boards/arm/kl/freedom-kl25z/src`)

## Overview
Board-level C implementation (`src`) for `freedom-kl25z` (`arm/kl`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[freedom-kl25z.h:kl_spidev_initialize]` Public declaration `kl_spidev_initialize()`
- `[freedom-kl25z.h:kl_usbinitialize]` Public declaration `kl_usbinitialize()`
- `[freedom-kl25z.h:kl_led_initialize]` Public declaration `kl_led_initialize()`
- `[freedom-kl25z.h:kl_pwm_setup]` Public declaration `kl_pwm_setup()`
- `[freedom-kl25z.h:GPIO_LED_R]` Hardware/board configuration macros (`GPIO_LED_R`, `GPIO_LED_G`, `GPIO_LED_B`)
- `[kl_adxl345.c:adxl345_interrupt]` Public function `adxl345_interrupt()`
- `[kl_adxl345.c:adxl345_archinitialize]` Public function `adxl345_archinitialize()`
- `[kl_boardinitialize.c:kl_boardinitialize]` Public function `kl_boardinitialize()`
- `[kl_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[kl_led.c:kl_led_initialize]` Public function `kl_led_initialize()`
- `[kl_led.c:board_autoled_on]` Public function `board_autoled_on()`
- `[kl_led.c:board_autoled_off]` Public function `board_autoled_off()`
- `[kl_pwm.c:kl_pwminitialize]` Public function `kl_pwminitialize()`
- `[kl_pwm.c:kl_pwm_setup]` Public function `kl_pwm_setup()`
- `[kl_spi.c:kl_spidev_initialize]` Public function `kl_spidev_initialize()`
- `[kl_spi.c:kl_spi0select]` Public function `kl_spi0select()`
- `[kl_spi.c:kl_spi1select]` Public function `kl_spi1select()`
- `[kl_spi.c:kl_spi0status]` Public function `kl_spi0status()`
- `[kl_spi.c:kl_spi1status]` Public function `kl_spi1status()`
- `[kl_spi.c:kl_spi0cmddata]` Public function `kl_spi0cmddata()`
- `[kl_spi.c:kl_spi1cmddata]` Public function `kl_spi1cmddata()`
- `[kl_tsi.c:kl_tsi_initialize]` Public function `kl_tsi_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_KL_SPI0`, `CONFIG_KL_SPI1`, `CONFIG_KL_TSI`, `CONFIG_KL_USBOTG`, `CONFIG_PWM` (+3 more)
- `[kl_adxl345.c:DEBUGASSERT]` Requires `priv`
- `[kl_adxl345.c:DEBUGASSERT]` Requires `minor == 0`
- `[kl_adxl345.c:#error]` Compile-time guard: `ADXL345 support requires CONFIG_KL_SPI0`
- `[kl_adxl345.c:#error]` Compile-time guard: `Only the ADXL345 SPI interface is supported`
- `[kl_pwm.c:kl_pwminitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[kl_tsi.c:kl_tsi_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[kl_adxl345.c:adxl345_interrupt]` Configures or drives hardware GPIO pins
- `[kl_adxl345.c:adxl345_interrupt]` Initializes/registers kernel devices or filesystems (`adxl345_register()`, `kl_spibus_initialize()`)
- `[kl_adxl345.c:adxl345_interrupt]` Modifies interrupt controller or critical-section state
- `[kl_boardinitialize.c:kl_boardinitialize]` Initializes/registers kernel devices or filesystems (`kl_led_initialize()`, `kl_spidev_initialize()`)
- `[kl_led.c:kl_led_initialize]` Configures or drives hardware GPIO pins
- `[kl_pwm.c:kl_pwminitialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[kl_spi.c:kl_spidev_initialize]` Configures or drives hardware GPIO pins
- `[kl_tsi.c:kl_tsi_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[kl_tsi.c:kl_tsi_initialize]` Configures or drives hardware GPIO pins
- `[kl_tsi.c:kl_tsi_initialize]` Initializes/registers kernel devices or filesystems (`register_driver()`)

## Verification
- Run: `./tools/configure.sh freedom-kl25z:nsh && make`
