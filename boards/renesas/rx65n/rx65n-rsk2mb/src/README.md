# `rx65n-rsk2mb/src` Component (`boards/renesas/rx65n/rx65n-rsk2mb/src`)

## Overview
Board-level C implementation (`src`) for `rx65n-rsk2mb` (`renesas/rx65n`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[rx65n_rsk2mb.h:rx65n_bringup]` Public declaration `rx65n_bringup()`
- `[rx65n_rsk2mb.h:rx65n_sbram_int]` Public declaration `rx65n_sbram_int()`
- `[rx65n_bringup.c:rx65n_bringup]` Public function `rx65n_bringup()`
- `[rx65n_bringup.c:board_autoled1_on]` Public function `board_autoled1_on()`
- `[rx65n_bringup.c:board_autoled2_on]` Public function `board_autoled2_on()`
- `[rx65n_bringup.c:board_autoled_on]` Public function `board_autoled_on()`
- `[rx65n_bringup.c:board_autoled1_off]` Public function `board_autoled1_off()`
- `[rx65n_bringup.c:board_autoled2_off]` Public function `board_autoled2_off()`
- `[rx65n_bringup.c:board_autoled_off]` Public function `board_autoled_off()`
- `[rx65n_bringup.c:board_late_initialize]` Public function `board_late_initialize()`
- `[rx65n_gpio.c:led_port_create]` Public function `led_port_create()`
- `[rx65n_gpio.c:sci_port_create]` Public function `sci_port_create()`
- `[rx65n_gpio.c:r_ether_pheriperal_enable]` Public function `r_ether_pheriperal_enable()`
- `[rx65n_gpio.c:r_usbdev_port_enable]` Public function `r_usbdev_port_enable()`
- `[rx65n_gpio.c:r_usb_port_enable]` Public function `r_usb_port_enable()`
- `[rx65n_gpio.c:sci1_init_port]` Public function `sci1_init_port()`
- `[rx65n_gpio.c:sci2_init_port]` Public function `sci2_init_port()`
- `[rx65n_gpio.c:sci8_init_port]` Public function `sci8_init_port()`
- `[rx65n_gpio.c:sci12_init_port]` Public function `sci12_init_port()`
- `[rx65n_gpio.c:rspi_pinconfig]` Public function `rspi_pinconfig()`
- `[rx65n_gpio.c:riic0_init_port]` Public function `riic0_init_port()`
- `[rx65n_gpio.c:riic1_init_port]` Public function `riic1_init_port()`
- `[rx65n_gpio.c:riic2_init_port]` Public function `riic2_init_port()`
- `[rx65n_sbram.c:rx65n_sbram_int]` Public function `rx65n_sbram_int()`
- *(+1 additional symbols across 4 files)*

## Invariants
- `[rx65n_bringup.c:rx65n_bringup]` Validates preconditions and returns `-ENODEV`, `-ENOEXEC`, `-ENOMEM` on failure
- `[rx65n_sbram.c:rx65n_sbram_int]` Validates preconditions and returns `-ENOSPC`, `-ENXIO` on failure

## Side Effects
- `[rx65n_bringup.c:rx65n_bringup]` Initializes/registers kernel devices or filesystems (`cdcacm_initialize()`, `i2c_register()`, `nx_mount()`, `rtc_driver_initialize()`, `rtc_initialize()`)
- `[rx65n_gpio.c:led_port_create]` Configures or drives hardware GPIO pins
- `[rx65n_sbram.c:rx65n_sbram_int]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh rx65n-rsk2mb:nsh && make`
