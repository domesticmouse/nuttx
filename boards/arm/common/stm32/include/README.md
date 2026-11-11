# `stm32/include` Component (`boards/arm/common/stm32/include`)

## Overview
Board-level public headers (`include`) for `stm32` (`arm/common`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 50 header file(s).

## Interface
- `[board_common.h:stm32_common_initialize]` Public declaration `stm32_common_initialize()`
- `[board_hall3ph.h:board_hall3ph_initialize]` Public declaration `board_hall3ph_initialize()`
- `[board_pwm.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[board_qencoder.h:board_qencoder_initialize]` Public declaration `board_qencoder_initialize()`
- `[board_sbutton.h:board_sbutton_initialize]` Public declaration `board_sbutton_initialize()`
- `[board_timer.h:stm32_timer_setup]` Public declaration `stm32_timer_setup()`
- `[stm32_amg88xx.h:board_amg88xx_initialize]` Public declaration `board_amg88xx_initialize()`
- `[stm32_apa102.h:board_apa102_initialize]` Public declaration `board_apa102_initialize()`
- `[stm32_apds9960.h:board_apds9960_initialize]` Public declaration `board_apds9960_initialize()`
- `[stm32_bh1750.h:board_bh1750_initialize]` Public declaration `board_bh1750_initialize()`
- `[stm32_bmi270.h:board_bmi270_initialize]` Public declaration `board_bmi270_initialize()`
- `[stm32_bmp180.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`
- `[stm32_bmp280.h:board_bmp280_initialize]` Public declaration `board_bmp280_initialize()`
- `[stm32_can_setup.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[stm32_cansock_setup.h:stm32_cansock_setup]` Public declaration `stm32_cansock_setup()`
- `[stm32_cs4344.h:board_cs4344_initialize]` Public declaration `board_cs4344_initialize()`
- `[stm32_dhtxx.h:board_dhtxx_initialize]` Public declaration `board_dhtxx_initialize()`
- `[stm32_drv8266.h:board_drv8825_initialize]` Public declaration `board_drv8825_initialize()`
- `[stm32_ds1307.h:board_ds1307_initialize]` Public declaration `board_ds1307_initialize()`
- `[stm32_hcsr04.h:board_hcsr04_initialize]` Public declaration `board_hcsr04_initialize()`
- `[stm32_ihm07m1.h:board_ihm07m1_initialize]` Public declaration `board_ihm07m1_initialize()`
- `[stm32_ihm08m1.h:board_ihm08m1_initialize]` Public declaration `board_ihm08m1_initialize()`
- `[stm32_ihm16m1.h:board_ihm16m1_initialize]` Public declaration `board_ihm16m1_initialize()`
- `[stm32_ina219.h:board_ina219_initialize]` Public declaration `board_ina219_initialize()`
- `[stm32_kmatrix_gpio.h:board_kmatrix_initialize]` Public declaration `board_kmatrix_initialize()`
- *(+27 additional symbols across 50 files)*

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
