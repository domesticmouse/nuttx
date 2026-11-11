# LED Driver Interfaces (`include/nuttx/leds`)

## Overview
Provides upper-half and lower-half driver interfaces for user LEDs, RGB LEDs, addressable LED strips, and LED matrix/controller ICs in NuttX. Includes the generic user LED character driver (`userled.h`), PWM-driven RGB LED driver (`rgbled.h`), and controller interfaces for APA102, WS2812, KTD2052, LP503X, MAX7219, NCP5623C, and PCA9635PW.

## Interface
- `userled.h:struct userled_lowerhalf_s`, `userled.h:struct userled_s`, `userled.h:struct userled_effect_sup_s`, `userled.h:struct userled_effect_set_s`, `userled.h:userled_set_t`, `userled.h:userled_register`, `userled.h:userled_lower_initialize`, `userled.h:ULEDIOC_SUPPORTED`, `userled.h:ULEDIOC_SETLED`, `userled.h:ULEDIOC_SETALL`, `userled.h:ULEDIOC_GETALL`, `userled.h:ULEDIOC_SUPEFFECT`, `userled.h:ULEDIOC_SETEFFECT`
- `rgbled.h:rgbled_register`
- `apa102.h:struct apa102_ledstrip_s`, `apa102.h:apa102_register`
- `ktd2052.h:struct ktd2052_mode_s`, `ktd2052.h:struct ktd2052_pattern_s`, `ktd2052.h:struct ktd2052_slots_s`, `ktd2052.h:ktd2052_register`, `ktd2052.h:KTDIOSETRGB`, `ktd2052.h:KTDIOSETMODE`
- `lp503x.h:struct lp503x_config_s`, `lp503x.h:lp503x_register`, `lp503x.h:PWMIOC_ENABLE`, `lp503x.h:PWMIOC_SET_LED_COLOUR`, `lp503x.h:PWMIOC_SET_RGB_COLOUR`
- `max7219.h:max7219_leds_register`
- `ncp5623c.h:struct ncp5623c_set_reg_s`, `ncp5623c.h:ncp5623c_register`, `ncp5623c.h:LEDIOC_SET_REG`
- `pca9635pw.h:struct pca9635pw_brightness_s`, `pca9635pw.h:pca9635pw_register`, `pca9635pw.h:PWMIOC_SETLED_BRIGHTNESS`
- `ws2812.h:struct ws2812_dev_s`, `ws2812.h:ws2812_register`, `ws2812.h:ws2812_leds_register`, `ws2812.h:ws2812_hsv_to_rgb`, `ws2812.h:ws2812_gamma_correct`

## Invariants
- `userled.h:userled_set_t` bitmasks are bounded by the set of supported LEDs returned by `userled.h:struct userled_lowerhalf_s` (`ll_supported`).
- `ws2812.h:struct ws2812_dev_s` requires mutual exclusion via `lock` (and `byte_order_lock` when `ws2812.h:CONFIG_WS2812_COMPONENT_TRANSFORM` is enabled) during pixel buffer updates.

## Side Effects
- Registration functions (`userled.h:userled_register`, `rgbled.h:rgbled_register`, `apa102.h:apa102_register`, `ktd2052.h:ktd2052_register`, `lp503x.h:lp503x_register`, `max7219.h:max7219_leds_register`, `ncp5623c.h:ncp5623c_register`, `pca9635pw.h:pca9635pw_register`, `ws2812.h:ws2812_register`) create VFS character device nodes.
- LED state mutations and ioctl commands trigger GPIO pin toggles, PWM duty updates, or SPI/I2C bus transactions to external LED controller hardware.

## Verification
- Run: `make test`
