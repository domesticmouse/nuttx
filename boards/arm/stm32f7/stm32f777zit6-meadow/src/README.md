# `stm32f777zit6-meadow/src` Component (`boards/arm/stm32f7/stm32f777zit6-meadow/src`)

## Overview
Board-level C implementation (`src`) for `stm32f777zit6-meadow` (`arm/stm32f7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f777zit6-meadow.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f777zit6-meadow.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32f777zit6-meadow.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f777zit6-meadow.h:arch_sporadic_initialize]` Public declaration `arch_sporadic_initialize()`
- `[stm32f777zit6-meadow.h:stm32_sdram_initialize]` Public declaration `stm32_sdram_initialize()`
- `[stm32f777zit6-meadow.h:stm32_disablefmc]` Public declaration `stm32_disablefmc()`
- `[stm32f777zit6-meadow.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[stm32f777zit6-meadow.h:init_corecomp]` Public declaration `init_corecomp()`
- `[stm32f777zit6-meadow.h:init_projectlab]` Public declaration `init_projectlab()`
- `[stm32f777zit6-meadow.h:stm32_quadspi_init]` Public declaration `stm32_quadspi_init()`
- `[stm32f777zit6-meadow.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `HAVE_SDIO`, `GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `GPIO_LED_GREEN` (+9 more))
- `[board_corecomp.c:init_corecomp]` Public function `init_corecomp()`
- `[board_projlab.c:init_projectlab]` Public function `init_projectlab()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_qspi_initialize]` Public function `stm32_qspi_initialize()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- *(+34 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_IDLE_CUSTOM`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_BOARD_MEADOW_F7_CORE_COMPUTE` (+13 more)
- `[board_projlab.c:#error]` Compile-time guard: `ProjectLab boards needs Light Sensor BH1750FVI enabled.`
- `[board_projlab.c:#error]` Compile-time guard: `ProjectLab boards needs Inertial Sensor BMI270 enabled.`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-ENOSYS` on failure
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[stm32_composite.c:DEBUGASSERT]` Requires `epin < STM32_NENDPOINTS`
- `[stm32_composite.c:DEBUGASSERT]` Requires `epout < STM32_NENDPOINTS`
- `[stm32_extmem.c:#error]` Compile-time guard: `Required GPIO ports not enabled`
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[board_corecomp.c:init_corecomp]` Initializes/registers kernel devices or filesystems (`stm32_sdio_initialize()`)
- `[board_projlab.c:init_projectlab]` Initializes/registers kernel devices or filesystems (`board_bh1750_initialize()`, `board_bmi270_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_qspi_initialize]` Initializes/registers kernel devices or filesystems (`arch_sporadic_initialize()`, `board_autoled_initialize()`, `stm32_sdram_initialize()`, `stm32_spidev_initialize()`, `w25qxxxjv_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_cs4344_initialize()`, `i2c_register()`, `nx_mount()`, `stm32_i2c_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[stm32_extmem.c:stm32_sdram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_extmem.c:stm32_sdram_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[stm32_sporadic.c:arch_sporadic_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32f777zit6-meadow:nsh && make`
