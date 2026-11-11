# `ev49n51a/src` Component (`boards/mips/pic32mz/ev49n51a/src`)

## Overview
Board-level C implementation (`src`) for `ev49n51a` (`mips/pic32mz`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[ev49n51a.h:pic32mz_bringup]` Public declaration `pic32mz_bringup()`
- `[ev49n51a.h:pic32mz_led_initialize]` Public declaration `pic32mz_led_initialize()`
- `[ev49n51a.h:pic32mz_spidev_initialize]` Public declaration `pic32mz_spidev_initialize()`
- `[ev49n51a.h:GPIO_LED_RED]` Hardware/board configuration macros (`GPIO_LED_RED`, `GPIO_LED_GREEN`, `GPIO_SST26_CS`, `GPIO_PHY_NRST`, `GPIO_PHY_NINT`, `SST26_MTD_MINOR` (+1 more))
- `[pic32mz_autoleds.c:pic32mz_led_initialize]` Public function `pic32mz_led_initialize()`
- `[pic32mz_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32mz_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Public function `pic32mz_boardinitialize()`
- `[pic32mz_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32mz_bringup.c:pic32mz_bringup]` Public function `pic32mz_bringup()`
- `[pic32mz_ethernet.c:arch_phy_irq]` Public function `arch_phy_irq()`
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Public function `pic32mz_spidev_initialize()`
- `[pic32mz_spi.c:pic32mz_spi1select]` Public function `pic32mz_spi1select()`
- `[pic32mz_spi.c:pic32mz_spi1status]` Public function `pic32mz_spi1status()`
- `[pic32mz_spi.c:pic32mz_spi1cmddata]` Public function `pic32mz_spi1cmddata()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_ETC_ROMFS`, `CONFIG_EV49N51A_PHY_INTERRUPT`, `CONFIG_PIC32MZ_SPI1`
- `[pic32mz_ethernet.c:DEBUGASSERT]` Requires `intf != NULL`
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[pic32mz_autoleds.c:pic32mz_led_initialize]` Configures or drives hardware GPIO pins
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Configures or drives hardware GPIO pins
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Initializes/registers kernel devices or filesystems (`pic32mz_led_initialize()`, `pic32mz_spidev_initialize()`)
- `[pic32mz_bringup.c:pic32mz_bringup]` Initializes/registers kernel devices or filesystems (`ftl_initialize()`, `nx_mount()`, `pic32mz_spibus_initialize()`, `pic32mz_wdt_initialize()`, `pic32mz_wlan_initialize()`)
- `[pic32mz_ethernet.c:arch_phy_irq]` Modifies interrupt controller or critical-section state
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ev49n51a:nsh && make`
