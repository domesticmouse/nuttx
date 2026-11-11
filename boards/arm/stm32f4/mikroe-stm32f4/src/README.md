# `mikroe-stm32f4/src` Component (`boards/arm/stm32f4/mikroe-stm32f4/src`)

## Overview
Board-level C implementation (`src`) for `mikroe-stm32f4` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[mikroe-stm32f4.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[mikroe-stm32f4.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[mikroe-stm32f4.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[mikroe-stm32f4.h:stm32_lcdinitialize]` Public declaration `stm32_lcdinitialize()`
- `[mikroe-stm32f4.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[mikroe-stm32f4.h:up_vs1053initialize]` Public declaration `up_vs1053initialize()`
- `[mikroe-stm32f4.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER`, `STM32F4DISCOVERY_PWMTIMER` (+35 more))
- `[etc_romfs.c:romfs_img]` Module symbol `romfs_img`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_clockconfig.c:stm32_board_clockconfig]` Public function `stm32_board_clockconfig()`
- `[stm32_extmem.c:stm32_extmemgpios]` Public function `stm32_extmemgpios()`
- `[stm32_extmem.c:stm32_extmemaddr]` Public function `stm32_extmemaddr()`
- `[stm32_extmem.c:stm32_extmemdata]` Public function `stm32_extmemdata()`
- `[stm32_idle.c:up_idle]` Public function `up_idle()`
- `[stm32_mio283qt2.c:stm32_lcdinitialize]` Public function `stm32_lcdinitialize()`
- `[stm32_mio283qt2.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_mio283qt2.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_mio283qt2.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[stm32_mio283qt9a.c:stm32_lcdinitialize]` Public function `stm32_lcdinitialize()`
- `[stm32_mio283qt9a.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_mio283qt9a.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_mio283qt9a.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- *(+19 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_STM32_CUSTOM_CLOCKCONFIG`, `CONFIG_ARCH_CUSTOM_PMINIT`, `CONFIG_ARCH_IDLE_CUSTOM`, `CONFIG_AUDIO_VS1053`, `CONFIG_ETC_ROMFS` (+6 more)
- `[mikroe-stm32f4.h:#error]` Compile-time guard: `The Mikroe-STM32F4 board does not support HOST OTG, only device!`
- `[stm32_extmem.c:#error]` Compile-time guard: `Required GPIO ports not enabled`
- `[stm32_mio283qt2.c:DEBUGASSERT]` Requires `lcddev == 0`
- `[stm32_mio283qt9a.c:DEBUGASSERT]` Requires `lcddev == 0`
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_touchscreen.c:DEBUGASSERT]` Requires `priv != NULL`
- `[stm32_touchscreen.c:DEBUGASSERT]` Requires `inode->i_private`
- `[stm32_touchscreen.c:#error]` Compile-time guard: `Touchpanel Input (CONFIG_INPUT=y) requires enablinga ADC2 (CONFIG_STM32_...`
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`
- `[stm32_vs1053.c:DEBUGASSERT]` Requires `priv->handler`

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `board_qencoder_initialize()`, `m25p_initialize()`, `mtdconfig_register()`, `rammtd_initialize()`)
- `[stm32_clockconfig.c:stm32_board_clockconfig]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_extmem.c:stm32_extmemgpios]` Configures or drives hardware GPIO pins
- `[stm32_idle.c:up_idle]` Modifies interrupt controller or critical-section state
- `[stm32_mio283qt2.c:stm32_lcdinitialize]` Configures or drives hardware GPIO pins
- `[stm32_mio283qt9a.c:stm32_lcdinitialize]` Configures or drives hardware GPIO pins
- `[stm32_pm.c:arm_pminitialize]` Initializes/registers kernel devices or filesystems (`pm_initialize()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_touchscreen.c:stm32_tsc_setup]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_touchscreen.c:stm32_tsc_setup]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh mikroe-stm32f4:nsh && make`
