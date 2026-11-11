# `pic32czca70-curiosity/src` Component (`boards/arm/samv7/pic32czca70-curiosity/src`)

## Overview
Board-level C implementation (`src`) for `pic32czca70-curiosity` (`arm/samv7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[sam_board.h:sam_usbinitialize]` Public declaration `sam_usbinitialize()`
- `[sam_board.h:sam_sdcard_initialize]` Public declaration `sam_sdcard_initialize()`
- `[sam_board.h:sam_flash_init]` Public declaration `sam_flash_init()`
- `[sam_board.h:sam_bringup]` Public declaration `sam_bringup()`
- `[sam_board.h:HAVE_LED_DRIVER]` Hardware/board configuration macros (`HAVE_LED_DRIVER`, `HAVE_HSMCI`, `HAVE_AUTOMOUNTER`, `HAVE_USB`, `HAVE_USBDEV`, `HAVE_PROGMEM_CHARDEV` (+15 more))
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
- `[sam_buttons.c:gpio_pins]` Exported global symbol `gpio_pins`
- `[sam_buttons.c:gpio_pins_int]` Exported global symbol `gpio_pins_int`
- `[sam_progmem_partition.c:sam_flash_init]` Public function `sam_flash_init()`
- `[sam_sdcard.c:sam_sdcard_initialize]` Public function `sam_sdcard_initialize()`
- `[sam_usbdev.c:sam_usbinitialize]` Public function `sam_usbinitialize()`
- `[sam_usbdev.c:sam_usbsuspend]` Public function `sam_usbsuspend()`
- `[sam_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[sam_userleds.c:board_userled]` Public function `board_userled()`
- *(+1 additional symbols across 10 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL`, `CONFIG_SAMV7_HSMCI0`, `CONFIG_SAMV7_PROGMEM` (+1 more)
- `[sam_board.h:#error]` Compile-time guard: `SAMV71 has only one MMC/SD slot (CONFIG_NSH_MMCSDSLOTNO)`
- `[sam_boardctl.c:board_ioctl]` Validates preconditions and returns `-EINVAL`, `-ENOTTY` on failure
- `[sam_boot.c:DEBUGASSERT]` Requires `frequency >= (BOARD_MAINOSC_FREQUENCY / 256)`
- `[sam_boot.c:DEBUGASSERT]` Requires `actual == frequency`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `btn_lower_initialize()`, `cdcacm_initialize()`, `nx_mount()`, `sam_sdcard_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_sdcard.c:sam_sdcard_initialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `sam_automount_initialize()`, `sam_hsmci_initialize()`)
- `[sam_usbdev.c:sam_usbinitialize]` Configures or drives hardware GPIO pins
- `[sam_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh pic32czca70-curiosity:nsh && make`
