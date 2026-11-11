# `stm32f769i-disco/src` Component (`boards/arm/stm32f7/stm32f769i-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32f769i-disco` (`arm/stm32f7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f769i-disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f769i-disco.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32f769i-disco.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f769i-disco.h:arch_sporadic_initialize]` Public declaration `arch_sporadic_initialize()`
- `[stm32f769i-disco.h:stm32_sdram_initialize]` Public declaration `stm32_sdram_initialize()`
- `[stm32f769i-disco.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `GPIO_LD3`, `GPIO_BTN_USER`, `GPIO_SCHED_HIGHPRI`, `GPIO_SCHED_RUNNING`, `STM32F769I_DISCO_PWMTIMER` (+1 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_extmem.c:stm32_sdram_initialize]` Public function `stm32_sdram_initialize()`
- `[stm32_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- *(+18 additional symbols across 10 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_PWM`, `CONFIG_SPORADIC_INSTRUMENTATION`, `CONFIG_STM32_FMC`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-ENOSYS` on failure
- `[stm32_extmem.c:#error]` Compile-time guard: `Required GPIO ports not enabled`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`arch_sporadic_initialize()`, `board_autoled_initialize()`, `stm32_sdram_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_extmem.c:stm32_sdram_initialize]` Configures or drives hardware GPIO pins
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_sporadic.c:arch_sporadic_initialize]` Configures or drives hardware GPIO pins
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32f769i-disco:nsh && make`
