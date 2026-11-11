# `rtl8720f_evb/src` Component (`boards/arm/rtl8720f/rtl8720f_evb/src`)

## Overview
Board-level C implementation (`src`) for `rtl8720f_evb` (`arm/rtl8720f`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_boardinitialize]` Public declaration `rtl8720f_boardinitialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_bringup]` Public declaration `rtl8720f_bringup()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_spi_initialize]` Public declaration `rtl8720f_spi_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_pwm_initialize]` Public declaration `rtl8720f_pwm_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_adc_initialize]` Public declaration `rtl8720f_adc_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_rtc_initialize]` Public declaration `rtl8720f_rtc_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_wdg_initialize]` Public declaration `rtl8720f_wdg_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_timer_initialize]` Public declaration `rtl8720f_timer_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_wifi_initialize]` Public declaration `rtl8720f_wifi_initialize()`
- `[rtl8720f_rtl8720f_evb.h:ameba_ipc_initialize]` Public declaration `ameba_ipc_initialize()`
- `[rtl8720f_rtl8720f_evb.h:ameba_flash_fs_initialize]` Public declaration `ameba_flash_fs_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_gpio_initialize]` Public declaration `rtl8720f_gpio_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_uart_initialize]` Public declaration `rtl8720f_uart_initialize()`
- `[rtl8720f_rtl8720f_evb.h:rtl8720f_i2c_initialize]` Public declaration `rtl8720f_i2c_initialize()`
- `[rtl8720f_adc.c:rtl8720f_adc_initialize]` Public function `rtl8720f_adc_initialize()`
- `[rtl8720f_boot.c:rtl8720f_boardinitialize]` Public function `rtl8720f_boardinitialize()`
- `[rtl8720f_boot.c:board_early_initialize]` Public function `board_early_initialize()`
- `[rtl8720f_bringup.c:rtos_critical_enter]` Public function `rtos_critical_enter()`
- `[rtl8720f_bringup.c:rtos_critical_exit]` Public function `rtos_critical_exit()`
- `[rtl8720f_bringup.c:rtos_time_delay_ms]` Public function `rtos_time_delay_ms()`
- `[rtl8720f_bringup.c:IPC_patch_function]` Public function `IPC_patch_function()`
- `[rtl8720f_bringup.c:IPC_SEMDelayStub]` Public function `IPC_SEMDelayStub()`
- `[rtl8720f_bringup.c:rtl8720f_bringup]` Public function `rtl8720f_bringup()`
- *(+10 additional symbols across 12 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_AMEBA_ADC`, `CONFIG_AMEBA_GPIO`, `CONFIG_AMEBA_I2C`, `CONFIG_AMEBA_PWM`, `CONFIG_AMEBA_RTC`, `CONFIG_AMEBA_SPI` (+3 more)
- `[rtl8720f_spi.c:rtl8720f_spi_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[rtl8720f_adc.c:rtl8720f_adc_initialize]` Initializes/registers kernel devices or filesystems (`ameba_adc_register()`)
- `[rtl8720f_bringup.c:rtos_critical_enter]` Initializes/registers kernel devices or filesystems (`ameba_flash_fs_initialize()`, `ameba_ipc_initialize()`, `nx_mount()`, `rtl8720f_adc_initialize()`, `rtl8720f_gpio_initialize()`)
- `[rtl8720f_gpio.c:rtl8720f_gpio_initialize]` Initializes/registers kernel devices or filesystems (`ameba_gpio_register()`)
- `[rtl8720f_i2c.c:rtl8720f_i2c_initialize]` Initializes/registers kernel devices or filesystems (`ameba_i2c_register()`)
- `[rtl8720f_pwm.c:rtl8720f_pwm_initialize]` Initializes/registers kernel devices or filesystems (`ameba_pwm_register()`)
- `[rtl8720f_rtc.c:rtl8720f_rtc_initialize]` Initializes/registers kernel devices or filesystems (`ameba_rtc_initialize()`)
- `[rtl8720f_spi.c:rtl8720f_spi_initialize]` Initializes/registers kernel devices or filesystems (`ameba_spi_register()`)
- `[rtl8720f_timer.c:rtl8720f_timer_initialize]` Initializes/registers kernel devices or filesystems (`ameba_timer_initialize()`)
- `[rtl8720f_uart.c:rtl8720f_uart_initialize]` Initializes/registers kernel devices or filesystems (`ameba_uart_register()`)
- `[rtl8720f_wdg.c:rtl8720f_wdg_initialize]` Initializes/registers kernel devices or filesystems (`ameba_wdg_initialize()`)

## Verification
- Run: `./tools/configure.sh rtl8720f_evb:nsh && make`
