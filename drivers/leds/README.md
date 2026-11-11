# LED Drivers (`drivers/leds`)

## Overview
Provides character driver upper-half abstractions and SPI/I2C/PWM lower-half peripheral drivers for discrete user LEDs, RGB LEDs, LED matrices, and addressable LED strips in NuttX.

## Interface
- `[userled_upper.c:userled_register]` - Registers an upper-half user LED character device bound to a `struct userled_lowerhalf_s` instance (`[userled_upper.c:struct userled_upperhalf_s]`).
- `[userled_lower.c:userled_lower_initialize]` - Initializes the generic board-level user LED lower-half driver (`[userled_lower.c:CONFIG_USERLED_LOWER]`).
- `[rgbled.c:rgbled_register]` - Registers a 3-channel PWM-driven RGB LED character driver (`[rgbled.c:struct rgbled_upperhalf_s]`).
- `[ws2812.c:ws2812_register]`, `[ws2812.c:ws2812_leds_register]`, `[ws2812.c:ws2812_write]`, `[ws2812.c:ws2812_read]`, `[ws2812.c:ws2812_hsv_to_rgb]`, `[ws2812.c:ws2812_gamma_correct]` - Addressable WS2812 RGB LED strip driver and color conversion helpers (`[ws2812.c:struct ws2812_dev_s]`).
- `[apa102.c:apa102_register]` - SPI driver for APA102 RGB LED strips (`[apa102.c:struct apa102_dev_s]`).
- `[ktd2052.c:ktd2052_initialize]`, `[ktd2052.c:ktd2052_register]` - I2C driver for the KTD2052 RGB LED controller (`[ktd2052.c:struct ktd2052_dev_s]`).
- `[lp503x.c:lp503x_register]` - I2C driver for TI LP5030/LP5036 30/36-channel LED controllers (`[lp503x.c:struct lp503x_dev_s]`).
- `[max7219.c:max7219_leds_register]` - SPI driver for MAX7219 8x8 LED matrix/digit display controllers (`[max7219.c:struct max7219_dev_s]`).
- `[ncp5623c.c:ncp5623c_register]` - I2C driver for ON Semiconductor NCP5623C triple LED controller (`[ncp5623c.c:struct ncp5623c_dev_s]`).
- `[pca9635pw.c:pca9635pw_register]` - I2C driver for NXP PCA9635PW 16-bit Fm+ LED controller (`[pca9635pw.c:struct pca9635pw_dev_s]`).

## Invariants
- Exclusive access to upper-half state and open-file lists is serialized via per-device mutexes (`[userled_upper.c:lu_lock]`, `[rgbled.c:nxmutex_lock]`, `[ws2812.c:nxmutex_lock]`).
- Lower-half operation tables and bus handles (`struct i2c_master_s`, `struct spi_dev_s`, `struct pwm_lowerhalf_s`) must be non-null prior to driver registration.

## Side Effects
- Registers VFS character device nodes via `register_driver` across all LED drivers (`[userled_upper.c:register_driver]`, `[ws2812.c:register_driver]`, `[rgbled.c:register_driver]`).
- Performs SPI bus locking and data transfers (`[apa102.c:SPI_SEND]`, `[max7219.c:CONFIG_SPI]`) and I2C transfers (`[ktd2052.c:I2C_TRANSFER]`, `[lp503x.c:CONFIG_I2C]`, `[ncp5623c.c:CONFIG_I2C]`, `[pca9635pw.c:CONFIG_I2C]`).

## Verification
- Run: `make test`
