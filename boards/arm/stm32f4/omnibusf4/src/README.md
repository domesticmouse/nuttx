# `omnibusf4/src` Component (`boards/arm/stm32f4/omnibusf4/src`)

## Overview
Board-level C implementation (`src`) for `omnibusf4` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 18 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[omnibusf4.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[omnibusf4.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[omnibusf4.h:stm32_mmcsd_initialize]` Public declaration `stm32_mmcsd_initialize()`
- `[omnibusf4.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[omnibusf4.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[omnibusf4.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[omnibusf4.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[omnibusf4.h:stm32_timer_driver_setup]` Public declaration `stm32_timer_driver_setup()`
- `[omnibusf4.h:stm32_mpu6000_initialize]` Public declaration `stm32_mpu6000_initialize()`
- `[omnibusf4.h:stm32_max7456_initialize]` Public declaration `stm32_max7456_initialize()`
- `[omnibusf4.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `SPIPORT_MPU6000`, `SPIMINOR_MPU6000`, `GPIO_CS_MPU6000`, `GPIO_EXTI_MPU6000`, `DEVNODE_MPU6000` (+5 more))
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_idle.c:up_idle]` Public function `up_idle()`
- `[stm32_ioctl.c:board_ioctl]` Public function `board_ioctl()`
- `[stm32_max7456.c:stm32_max7456_initialize]` Public function `stm32_max7456_initialize()`
- `[stm32_mmcsd.c:stm32_spi2register]` Public function `stm32_spi2register()`
- `[stm32_mmcsd.c:stm32_mmcsd_initialize]` Public function `stm32_mmcsd_initialize()`
- `[stm32_mpu6000.c:stm32_mpu6000_initialize]` Public function `stm32_mpu6000_initialize()`
- `[stm32_netinit.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[stm32_pm.c:arm_pminitialize]` Public function `arm_pminitialize()`
- `[stm32_pwm.c:stm32_pwm_setup]` Public function `stm32_pwm_setup()`
- *(+20 additional symbols across 18 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_CUSTOM_PMINIT`, `CONFIG_ARCH_IDLE_CUSTOM`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARDCTL_UNIQUEID` (+8 more)
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENOMEM` on failure
- `[stm32_ioctl.c:board_ioctl]` Validates preconditions and returns `-ENOTTY` on failure
- `[stm32_max7456.c:stm32_max7456_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_mmcsd.c:#error]` Compile-time guard: `SD driver requires CONFIG_DISABLE_MOUNTPOINT to be disabled`
- `[stm32_mpu6000.c:stm32_mpu6000_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `ccm_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `nx_mount()`, `rtc_initialize()`, `stm32_i2c_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_idle.c:up_idle]` Modifies interrupt controller or critical-section state
- `[stm32_max7456.c:stm32_max7456_initialize]` Configures or drives hardware GPIO pins
- `[stm32_max7456.c:stm32_max7456_initialize]` Initializes/registers kernel devices or filesystems (`max7456_register()`, `stm32_spibus_initialize()`)
- `[stm32_mmcsd.c:stm32_spi2register]` Configures or drives hardware GPIO pins
- `[stm32_mmcsd.c:stm32_spi2register]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)
- `[stm32_mpu6000.c:stm32_mpu6000_initialize]` Configures or drives hardware GPIO pins
- `[stm32_mpu6000.c:stm32_mpu6000_initialize]` Initializes/registers kernel devices or filesystems (`mpu60x0_register()`, `stm32_spibus_initialize()`)
- `[stm32_pm.c:arm_pminitialize]` Initializes/registers kernel devices or filesystems (`pm_initialize()`)
- `[stm32_pwm.c:stm32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh omnibusf4:nsh && make`
