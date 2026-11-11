# `cloudctrl/src` Component (`boards/arm/stm32f1/cloudctrl/src`)

## Overview
Board-level C implementation (`src`) for `cloudctrl` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[cloudctrl.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[cloudctrl.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[cloudctrl.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[cloudctrl.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[cloudctrl.h:stm32_sdinitialize]` Public declaration `stm32_sdinitialize()`
- `[cloudctrl.h:stm32_w25initialize]` Public declaration `stm32_w25initialize()`
- `[cloudctrl.h:GPIO_MII_INT]` Hardware/board configuration macros (`GPIO_MII_INT`, `GPIO_DM9161_RET`, `GPIO_WIRELESS_CS`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS` (+12 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_autoleds.c:up_ledpminitialize]` Public function `up_ledpminitialize()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_chipid.c:stm32_getchipid]` Public function `stm32_getchipid()`
- `[stm32_chipid.c:stm32_getchipid_string]` Public function `stm32_getchipid_string()`
- `[stm32_phyinit.c:stm32_phy_boardinitialize]` Public function `stm32_phy_boardinitialize()`
- `[stm32_relays.c:up_relaysinit]` Public function `up_relaysinit()`
- `[stm32_relays.c:relays_setstat]` Public function `relays_setstat()`
- `[stm32_relays.c:relays_getstat]` Public function `relays_getstat()`
- *(+23 additional symbols across 13 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_ARCH_RELAYS`, `CONFIG_MTD_W25` (+3 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`
- `[stm32_w25.c:stm32_w25initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_autoleds.c:board_autoled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`, `stm32_usbhost_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_phyinit.c:stm32_phy_boardinitialize]` Configures or drives hardware GPIO pins
- `[stm32_relays.c:up_relaysinit]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_otgfshost_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_msc_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh cloudctrl:nsh && make`
