# `devebox-stm32h743/src` Component (`boards/arm/stm32h7/devebox-stm32h743/src`)

## Overview
Board-level C implementation (`src`) for `devebox-stm32h743` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[devebox-stm32h743.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[devebox-stm32h743.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[devebox-stm32h743.h:stm32_dma_alloc_init]` Public declaration `stm32_dma_alloc_init()`
- `[devebox-stm32h743.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[devebox-stm32h743.h:stm32_w25qxxx_setup]` Public declaration `stm32_w25qxxx_setup()`
- `[devebox-stm32h743.h:board_dac_initialize]` Public declaration `board_dac_initialize()`
- `[devebox-stm32h743.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBHOST`, `STM32_PROCFS_MOUNTPOINT`, `HAVE_RTC_DRIVER`, `GPIO_LD1`, `GPIO_BTN1_USER` (+5 more))
- `[stm32_gpio_helper.h:gpio_helper_reg_output]` Public declaration `gpio_helper_reg_output()`
- `[stm32_gpio_helper.h:gpio_helper_reg_input]` Public declaration `gpio_helper_reg_input()`
- `[stm32_gpio_helper.h:gpio_helper_reg_input_interrupt]` Public declaration `gpio_helper_reg_input_interrupt()`
- `[stm32_gpio_helper.h:gpio_helper_mode_e]` Type definition `gpio_helper_mode_e`
- `[stm32_gpio_helper.h:gpio_helper_pull_e]` Type definition `gpio_helper_pull_e`
- `[stm32_appinitialize.c:board_app_initialize]` Public function `board_app_initialize()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_dac_init.c:board_dac_initialize]` Public function `board_dac_initialize()`
- *(+13 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DAC`, `CONFIG_DEV_GPIO`, `CONFIG_FAT_DMAMEMORY` (+2 more)
- `[stm32_bringup.c:#error]` Compile-time guard: `CONFLICT: OTGFS_ID pin uses PA10, which is also USART1 RX. \`
- `[stm32_bringup.c:#error]` Compile-time guard: `CONFLICT: OTGHS_ID pin uses PA10, which is also USART1 RX. \`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_dac_init.c:board_dac_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_dma_alloc.c:#error]` Compile-time guard: `microSD DMA support requires CONFIG_GRAN`
- `[stm32_gpio_helper.c:gpio_helper_reg_output]` Validates preconditions and returns `-EINVAL`, `-ENOMEM`, `-ENOSYS` on failure
- `[stm32_ioctl.c:board_ioctl]` Validates preconditions and returns `-ENOTTY` on failure
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `board_dac_initialize()`, `btn_lower_initialize()`, `cdcacm_initialize()`, `nx_mount()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_dac_init.c:board_dac_initialize]` Initializes/registers kernel devices or filesystems (`dac_register()`)
- `[stm32_dma_alloc.c:stm32_dma_alloc_init]` Initializes/registers kernel devices or filesystems (`gran_initialize()`)
- `[stm32_gpio_helper.c:gpio_helper_reg_output]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_gpio_helper.c:gpio_helper_reg_output]` Configures or drives hardware GPIO pins
- `[stm32_gpio_helper.c:gpio_helper_reg_output]` Modifies interrupt controller or critical-section state
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_usb.c:stm32_usbhost_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh devebox-stm32h743:nsh && make`
