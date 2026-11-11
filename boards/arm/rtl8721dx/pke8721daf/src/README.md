# `pke8721daf/src` Component (`boards/arm/rtl8721dx/pke8721daf/src`)

## Overview
Board-level C implementation (`src`) for `pke8721daf` (`arm/rtl8721dx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rtl8721dx_pke8721daf.h:rtl8721dx_boardinitialize]` Public declaration `rtl8721dx_boardinitialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_bringup]` Public declaration `rtl8721dx_bringup()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_wifi_initialize]` Public declaration `rtl8721dx_wifi_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_gpio_initialize]` Public declaration `rtl8721dx_gpio_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_uart_initialize]` Public declaration `rtl8721dx_uart_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_i2c_initialize]` Public declaration `rtl8721dx_i2c_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_spi_initialize]` Public declaration `rtl8721dx_spi_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_pwm_initialize]` Public declaration `rtl8721dx_pwm_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_adc_initialize]` Public declaration `rtl8721dx_adc_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_rtc_initialize]` Public declaration `rtl8721dx_rtc_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_wdg_initialize]` Public declaration `rtl8721dx_wdg_initialize()`
- `[rtl8721dx_pke8721daf.h:rtl8721dx_timer_initialize]` Public declaration `rtl8721dx_timer_initialize()`
- `[rtl8721dx_pke8721daf.h:ameba_flash_fs_initialize]` Public declaration `ameba_flash_fs_initialize()`
- `[rtl8721dx_adc.c:rtl8721dx_adc_initialize]` Public function `rtl8721dx_adc_initialize()`
- `[rtl8721dx_boot.c:rtl8721dx_boardinitialize]` Public function `rtl8721dx_boardinitialize()`
- `[rtl8721dx_boot.c:board_early_initialize]` Public function `board_early_initialize()`
- `[rtl8721dx_bringup.c:rtos_critical_enter]` Public function `rtos_critical_enter()`
- `[rtl8721dx_bringup.c:rtos_critical_exit]` Public function `rtos_critical_exit()`
- `[rtl8721dx_bringup.c:rtos_time_delay_ms]` Public function `rtos_time_delay_ms()`
- `[rtl8721dx_bringup.c:IPC_patch_function]` Public function `IPC_patch_function()`
- `[rtl8721dx_bringup.c:IPC_SEMDelay]` Public function `IPC_SEMDelay()`
- `[rtl8721dx_bringup.c:rtl8721dx_bringup]` Public function `rtl8721dx_bringup()`
- `[rtl8721dx_bringup.c:board_app_initialize]` Public function `board_app_initialize()`
- *(+9 additional symbols across 12 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_AMEBA_ADC`, `CONFIG_AMEBA_GPIO`, `CONFIG_AMEBA_I2C`, `CONFIG_AMEBA_PWM`, `CONFIG_AMEBA_RTC`, `CONFIG_AMEBA_SPI` (+3 more)
- `[rtl8721dx_spi.c:rtl8721dx_spi_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[rtl8721dx_adc.c:rtl8721dx_adc_initialize]` Initializes/registers kernel devices or filesystems (`ameba_adc_register()`)
- `[rtl8721dx_bringup.c:rtos_critical_enter]` Initializes/registers kernel devices or filesystems (`ameba_flash_fs_initialize()`, `nx_mount()`, `rtl8721dx_adc_initialize()`, `rtl8721dx_gpio_initialize()`, `rtl8721dx_i2c_initialize()`)
- `[rtl8721dx_gpio.c:rtl8721dx_gpio_initialize]` Initializes/registers kernel devices or filesystems (`ameba_gpio_register()`)
- `[rtl8721dx_i2c.c:rtl8721dx_i2c_initialize]` Initializes/registers kernel devices or filesystems (`ameba_i2c_register()`)
- `[rtl8721dx_pwm.c:rtl8721dx_pwm_initialize]` Initializes/registers kernel devices or filesystems (`ameba_pwm_register()`)
- `[rtl8721dx_rtc.c:rtl8721dx_rtc_initialize]` Initializes/registers kernel devices or filesystems (`ameba_rtc_initialize()`)
- `[rtl8721dx_spi.c:rtl8721dx_spi_initialize]` Initializes/registers kernel devices or filesystems (`ameba_spi_register()`)
- `[rtl8721dx_timer.c:rtl8721dx_timer_initialize]` Initializes/registers kernel devices or filesystems (`ameba_timer_initialize()`)
- `[rtl8721dx_uart.c:rtl8721dx_uart_initialize]` Initializes/registers kernel devices or filesystems (`ameba_uart_register()`)
- `[rtl8721dx_wdg.c:rtl8721dx_wdg_initialize]` Initializes/registers kernel devices or filesystems (`ameba_wdg_initialize()`)

## Verification
- Run: `./tools/configure.sh pke8721daf:nsh && make`
