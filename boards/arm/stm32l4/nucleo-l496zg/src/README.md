# `nucleo-l496zg/src` Component (`boards/arm/stm32l4/nucleo-l496zg/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-l496zg` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-144.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-144.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-144.h:stm32_spidev_bus_test]` Public declaration `stm32_spidev_bus_test()`
- `[nucleo-144.h:stm32_dma_alloc_init]` Public declaration `stm32_dma_alloc_init()`
- `[nucleo-144.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[nucleo-144.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[nucleo-144.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-144.h:stm32_dac_setup]` Public declaration `stm32_dac_setup()`
- `[nucleo-144.h:stm32_dfsdm_setup]` Public declaration `stm32_dfsdm_setup()`
- `[nucleo-144.h:GPIO_LD1]` Hardware/board configuration macros (`GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `GPIO_LED_GREEN`, `GPIO_LED_BLUE`, `GPIO_LED_RED` (+23 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_dac.c:stm32_dac_setup]` Public function `stm32_dac_setup()`
- `[stm32_dfsdm.c:stm32_dfsdm_setup]` Public function `stm32_dfsdm_setup()`
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Public function `stm32_dma_alloc_init()`
- *(+25 additional symbols across 16 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_BOARDCTL_UNIQUEID` (+7 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_dac.c:stm32_dac_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_dfsdm.c:stm32_dfsdm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_dma_alloc.c:#error]` Compile-time guard: `microSD DMA support requires CONFIG_GRAN`
- `[stm32_ioctl.c:board_ioctl]` Validates preconditions and returns `-ENOTTY` on failure
- `[stm32_sdio.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:#error]` Compile-time guard: `No CONFIG_NUCLEO_SPI1_TEST_MODEx defined`
- `[stm32_spi.c:#error]` Compile-time guard: `No CONFIG_NUCLEO_SPI2_TEST_MODEx defined`
- `[stm32_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_adc_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`stm32_common_initialize()`, `stm32_sdio_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_dac.c:stm32_dac_setup]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[stm32_dfsdm.c:stm32_dfsdm_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_dfsdm_initialize()`)
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Initializes/registers kernel devices or filesystems (`gran_initialize()`)
- `[stm32_sdio.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdio.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-l496zg:nsh && make`
