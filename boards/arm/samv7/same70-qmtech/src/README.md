# `same70-qmtech/src` Component (`boards/arm/samv7/same70-qmtech/src`)

## Overview
Board-level C implementation (`src`) for `same70-qmtech` (`arm/samv7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[same70-qmtech.h:sam_bringup]` Public declaration `sam_bringup()`
- `[same70-qmtech.h:sam_afec_setup]` Public declaration `sam_afec_setup()`
- `[same70-qmtech.h:sam_dacdev_initialize]` Public declaration `sam_dacdev_initialize()`
- `[same70-qmtech.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[same70-qmtech.h:sam_can_setup]` Public declaration `sam_can_setup()`
- `[same70-qmtech.h:sam_gpio_initialize]` Public declaration `sam_gpio_initialize()`
- `[same70-qmtech.h:HAVE_HSMCI]` Hardware/board configuration macros (`HAVE_HSMCI`, `HAVE_AUTOMOUNTER`, `HAVE_PROGMEM_CHARDEV`, `CONFIG_NSH_MMCSDMINOR`, `CONFIG_NSH_MMCSDSLOTNO`, `HSMCI0_SLOTNO` (+11 more))
- `[sam_afec.c:sam_afec_setup]` Public function `sam_afec_setup()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boardctl.c:board_ioctl]` Public function `board_ioctl()`
- `[sam_boardctl.c:board_uniqueid]` Public function `board_uniqueid()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sam_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sam_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sam_dac.c:sam_dacdev_initialize]` Public function `sam_dacdev_initialize()`
- `[sam_gpio.c:sam_gpio_initialize]` Public function `sam_gpio_initialize()`
- `[sam_mcan.c:sam_can_setup]` Public function `sam_can_setup()`
- `[sam_spi.c:sam_spidev_initialize]` Public function `sam_spidev_initialize()`
- `[sam_spi.c:sam_spi0select]` Public function `sam_spi0select()`
- *(+6 additional symbols across 12 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL`, `CONFIG_DEV_GPIO`, `CONFIG_SAMV7_AFEC` (+4 more)
- `[same70-qmtech.h:#error]` Compile-time guard: `SAME70 has only one MMC/SD slot (CONFIG_NSH_MMCSDSLOTNO)`
- `[sam_afec.c:sam_afec_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_boardctl.c:board_ioctl]` Validates preconditions and returns `-EINVAL`, `-ENOTTY` on failure
- `[sam_boot.c:DEBUGASSERT]` Requires `frequency >= (BOARD_MAINOSC_FREQUENCY / 256)`
- `[sam_boot.c:DEBUGASSERT]` Requires `actual == frequency`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_dac.c:sam_dacdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_gpio.c:DEBUGASSERT]` Requires `samgpio != NULL && value != NULL`
- `[sam_gpio.c:DEBUGASSERT]` Requires `samgpio->id < BOARD_NGPIOIN`
- `[sam_mcan.c:sam_can_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[sam_afec.c:sam_afec_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `sam_afec_initialize()`)
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_spidev_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `btn_lower_initialize()`, `nx_mount()`, `romdisk_register()`, `sam_automount_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_dac.c:sam_dacdev_initialize]` Initializes/registers kernel devices or filesystems (`dac_register()`, `sam_dac_initialize()`)
- `[sam_gpio.c:sam_gpio_initialize]` Configures or drives hardware GPIO pins
- `[sam_gpio.c:sam_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[sam_gpio.c:sam_gpio_initialize]` Modifies interrupt controller or critical-section state
- `[sam_mcan.c:sam_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`, `sam_mcan_initialize()`)
- `[sam_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh same70-qmtech:nsh && make`
