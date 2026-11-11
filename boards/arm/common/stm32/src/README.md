# `stm32/src` Component (`boards/arm/common/stm32/src`)

## Overview
Board-level C implementation (`src`) for `stm32` (`arm/common`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 51 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[board_common.c:stm32_common_initialize]` Public function `stm32_common_initialize()`
- `[board_hall3ph.c:board_hall3ph_initialize]` Public function `board_hall3ph_initialize()`
- `[board_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- `[board_qencoder.c:board_qencoder_initialize]` Public function `board_qencoder_initialize()`
- `[board_timer.c:stm32_timer_setup]` Public function `stm32_timer_setup()`
- `[stm32_amg88xx.c:board_amg88xx_initialize]` Public function `board_amg88xx_initialize()`
- `[stm32_apa102.c:board_apa102_initialize]` Public function `board_apa102_initialize()`
- `[stm32_apds9960.c:board_apds9960_initialize]` Public function `board_apds9960_initialize()`
- `[stm32_bh1750.c:board_bh1750_initialize]` Public function `board_bh1750_initialize()`
- `[stm32_bmi270.c:board_bmi270_initialize]` Public function `board_bmi270_initialize()`
- `[stm32_bmp180.c:board_bmp180_initialize]` Public function `board_bmp180_initialize()`
- `[stm32_bmp280.c:board_bmp280_initialize]` Public function `board_bmp280_initialize()`
- `[stm32_can_setup.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_cansock_setup.c:stm32_cansock_setup]` Public function `stm32_cansock_setup()`
- `[stm32_cs4344.c:board_cs4344_initialize]` Public function `board_cs4344_initialize()`
- `[stm32_dhtxx.c:board_dhtxx_initialize]` Public function `board_dhtxx_initialize()`
- `[stm32_drv8825.c:board_drv8825_initialize]` Public function `board_drv8825_initialize()`
- `[stm32_ds1307.c:board_ds1307_initialize]` Public function `board_ds1307_initialize()`
- `[stm32_hcsr04.c:board_hcsr04_initialize]` Public function `board_hcsr04_initialize()`
- `[stm32_ihm07m1.c:board_ihm07m1_initialize]` Public function `board_ihm07m1_initialize()`
- `[stm32_ihm07m1.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_ihm08m1.c:board_ihm08m1_initialize]` Public function `board_ihm08m1_initialize()`
- `[stm32_ihm08m1.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- *(+38 additional symbols across 51 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_AUDIO_CS4344`, `CONFIG_AUDIO_TONE`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARD_STM32_IHM07M1`, `CONFIG_BOARD_STM32_IHM08M1` (+51 more)
- `[board_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[board_timer.c:stm32_timer_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_amg88xx.c:board_amg88xx_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_apa102.c:board_apa102_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_apds9960.c:board_apds9960_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bh1750.c:board_bh1750_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bmi270.c:board_bmi270_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bmp180.c:board_bmp180_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bmp280.c:board_bmp280_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_can_setup.c:#error]` Compile-time guard: `No CAN is enabled. Please enable at least one CAN device`
- `[stm32_cansock_setup.c:#error]` Compile-time guard: `No CAN is enabled. Please enable at least one CAN device`

## Side Effects
- `[board_common.c:stm32_common_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nx_mount()`, `stm32_i2c_register()`, `stm32_i2cbus_initialize()`)
- `[board_hall3ph.c:board_hall3ph_initialize]` Initializes/registers kernel devices or filesystems (`stm32_hall3ph_initialize()`)
- `[board_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[board_timer.c:stm32_timer_setup]` Initializes/registers kernel devices or filesystems (`oneshot_initialize()`, `oneshot_register()`, `stm32_lptim_oneshot_initialize()`, `stm32_lptim_timer_initialize()`, `stm32_timer_initialize()`)
- `[stm32_amg88xx.c:board_amg88xx_initialize]` Initializes/registers kernel devices or filesystems (`amg88xx_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_apa102.c:board_apa102_initialize]` Initializes/registers kernel devices or filesystems (`apa102_register()`, `stm32_spibus_initialize()`)
- `[stm32_apds9960.c:board_apds9960_initialize]` Configures or drives hardware GPIO pins
- `[stm32_apds9960.c:board_apds9960_initialize]` Initializes/registers kernel devices or filesystems (`apds9960_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_apds9960.c:board_apds9960_initialize]` Modifies interrupt controller or critical-section state
- `[stm32_bh1750.c:board_bh1750_initialize]` Initializes/registers kernel devices or filesystems (`bh1750fvi_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_bmi270.c:board_bmi270_initialize]` Initializes/registers kernel devices or filesystems (`bmi270_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_bmp180.c:board_bmp180_initialize]` Initializes/registers kernel devices or filesystems (`bmp180_register()`, `stm32_i2cbus_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
