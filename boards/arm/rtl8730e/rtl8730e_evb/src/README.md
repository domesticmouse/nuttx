# `rtl8730e_evb/src` Component (`boards/arm/rtl8730e/rtl8730e_evb/src`)

## Overview
Board-level C implementation (`src`) for `rtl8730e_evb` (`arm/rtl8730e`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rtl8730e_evb.h:rtl8730e_bringup]` Public declaration `rtl8730e_bringup()`
- `[rtl8730e_evb.h:rtl8730e_gpio_initialize]` Public declaration `rtl8730e_gpio_initialize()`
- `[rtl8730e_evb.h:rtl8730e_uart_initialize]` Public declaration `rtl8730e_uart_initialize()`
- `[rtl8730e_evb.h:rtl8730e_i2c_initialize]` Public declaration `rtl8730e_i2c_initialize()`
- `[rtl8730e_evb.h:rtl8730e_spi_initialize]` Public declaration `rtl8730e_spi_initialize()`
- `[rtl8730e_evb.h:rtl8730e_pwm_initialize]` Public declaration `rtl8730e_pwm_initialize()`
- `[rtl8730e_evb.h:rtl8730e_timer_initialize]` Public declaration `rtl8730e_timer_initialize()`
- `[rtl8730e_evb.h:rtl8730e_wdg_initialize]` Public declaration `rtl8730e_wdg_initialize()`
- `[rtl8730e_evb.h:rtl8730e_adc_initialize]` Public declaration `rtl8730e_adc_initialize()`
- `[rtl8730e_evb.h:rtl8730e_rtc_initialize]` Public declaration `rtl8730e_rtc_initialize()`
- `[rtl8730e_adc.c:rtl8730e_adc_initialize]` Public function `rtl8730e_adc_initialize()`
- `[rtl8730e_boardinit.c:rtl8730e_memory_initialize]` Public function `rtl8730e_memory_initialize()`
- `[rtl8730e_boardinit.c:rtl8730e_board_initialize]` Public function `rtl8730e_board_initialize()`
- `[rtl8730e_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rtl8730e_boardinit.c:board_power_off]` Public function `board_power_off()`
- `[rtl8730e_bringup.c:rtl8730e_wifi_initialize]` Public function `rtl8730e_wifi_initialize()`
- `[rtl8730e_bringup.c:rtl8730e_bringup]` Public function `rtl8730e_bringup()`
- `[rtl8730e_gpio.c:rtl8730e_gpio_initialize]` Public function `rtl8730e_gpio_initialize()`
- `[rtl8730e_i2c.c:rtl8730e_i2c_initialize]` Public function `rtl8730e_i2c_initialize()`
- `[rtl8730e_pwm.c:rtl8730e_pwm_initialize]` Public function `rtl8730e_pwm_initialize()`
- `[rtl8730e_rtc.c:rtl8730e_rtc_initialize]` Public function `rtl8730e_rtc_initialize()`
- `[rtl8730e_spi.c:rtl8730e_spi_initialize]` Public function `rtl8730e_spi_initialize()`
- `[rtl8730e_timer.c:rtl8730e_timer_initialize]` Public function `rtl8730e_timer_initialize()`
- *(+2 additional symbols across 12 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_AMEBA_ADC`, `CONFIG_AMEBA_GPIO`, `CONFIG_AMEBA_I2C`, `CONFIG_AMEBA_PWM`, `CONFIG_AMEBA_RTC`, `CONFIG_AMEBA_SPI` (+7 more)
- `[rtl8730e_bringup.c:rtl8730e_wifi_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[rtl8730e_spi.c:rtl8730e_spi_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[rtl8730e_adc.c:rtl8730e_adc_initialize]` Initializes/registers kernel devices or filesystems (`ameba_adc_register()`)
- `[rtl8730e_bringup.c:rtl8730e_wifi_initialize]` Initializes/registers kernel devices or filesystems (`ameba_flash_fs_initialize()`, `fdt_cfi_register()`, `fdt_pci_ecam_register()`, `fdt_virtio_mmio_devices_register()`, `nx_mount()`)
- `[rtl8730e_gpio.c:rtl8730e_gpio_initialize]` Initializes/registers kernel devices or filesystems (`ameba_gpio_register()`)
- `[rtl8730e_i2c.c:rtl8730e_i2c_initialize]` Initializes/registers kernel devices or filesystems (`ameba_i2c_register()`)
- `[rtl8730e_pwm.c:rtl8730e_pwm_initialize]` Initializes/registers kernel devices or filesystems (`ameba_pwm_register()`)
- `[rtl8730e_rtc.c:rtl8730e_rtc_initialize]` Initializes/registers kernel devices or filesystems (`ameba_rtc_initialize()`)
- `[rtl8730e_spi.c:rtl8730e_spi_initialize]` Initializes/registers kernel devices or filesystems (`ameba_spi_register()`)
- `[rtl8730e_timer.c:rtl8730e_timer_initialize]` Initializes/registers kernel devices or filesystems (`ameba_timer_initialize()`)
- `[rtl8730e_uart.c:rtl8730e_uart_initialize]` Initializes/registers kernel devices or filesystems (`ameba_uart_register()`)
- `[rtl8730e_wdg.c:rtl8730e_wdg_initialize]` Initializes/registers kernel devices or filesystems (`ameba_wdg_initialize()`)

## Verification
- Run: `./tools/configure.sh rtl8730e_evb:nsh && make`
