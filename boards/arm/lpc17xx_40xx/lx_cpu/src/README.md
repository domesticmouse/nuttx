# `lx_cpu/src` Component (`boards/arm/lpc17xx_40xx/lx_cpu/src`)

## Overview
Board-level C implementation (`src`) for `lx_cpu` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[lx_cpu.h:lx_cpu_bringup]` Public declaration `lx_cpu_bringup()`
- `[lx_cpu.h:lx_cpu_sspdev_initialize]` Public declaration `lx_cpu_sspdev_initialize()`
- `[lx_cpu.h:lx_cpu_sdram_initialize]` Public declaration `lx_cpu_sdram_initialize()`
- `[lx_cpu.h:lx_cpu_fpga_initialize]` Public declaration `lx_cpu_fpga_initialize()`
- `[lx_cpu.h:lx_cpu_can_setup]` Public declaration `lx_cpu_can_setup()`
- `[lx_cpu.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_SD_CD`, `GPIO_LCD_BL`, `GPIO_TC_PENIRQ`, `GPIO_TC_BUSY` (+2 more))
- `[lpc17_40_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc17_40_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_boardinitialize.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boardinitialize.c:board_initialize]` Public function `board_initialize()`
- `[lpc17_40_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_bringup.c:lx_cpu_bringup]` Public function `lx_cpu_bringup()`
- `[lpc17_40_can.c:lx_cpu_can_setup]` Public function `lx_cpu_can_setup()`
- `[lpc17_40_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[lpc17_40_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[lpc17_40_fpgainitialize.c:lx_cpu_fpga_initialize]` Public function `lx_cpu_fpga_initialize()`
- `[lpc17_40_reset.c:board_reset]` Public function `board_reset()`
- `[lpc17_40_sdraminitialize.c:lx_cpu_sdram_initialize]` Public function `lx_cpu_sdram_initialize()`
- `[lpc17_40_ssp.c:lx_cpu_sspdev_initialize]` Public function `lx_cpu_sspdev_initialize()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0select]` Public function `lpc17_40_ssp0select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0status]` Public function `lpc17_40_ssp0status()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1select]` Public function `lpc17_40_ssp1select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1status]` Public function `lpc17_40_ssp1status()`
- *(+6 additional symbols across 12 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_CAN`, `CONFIG_LPC17_40_EMC`, `CONFIG_LPC17_40_EXTDRAM`, `CONFIG_USBDEV_COMPOSITE`
- `[lpc17_40_bringup.c:lx_cpu_bringup]` Validates preconditions and returns `-ENODEV`, `-ENOEXEC` on failure
- `[lpc17_40_can.c:lx_cpu_can_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[lpc17_40_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_boardinitialize.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lx_cpu_fpga_initialize()`, `lx_cpu_sdram_initialize()`, `lx_cpu_sspdev_initialize()`)
- `[lpc17_40_bringup.c:lx_cpu_bringup]` Configures or drives hardware GPIO pins
- `[lpc17_40_bringup.c:lx_cpu_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `lpc17_40_usbhost_initialize()`, `nx_mount()`, `sdio_initialize()`, `usbhost_cdcacm_initialize()`)
- `[lpc17_40_bringup.c:lx_cpu_bringup]` Modifies interrupt controller or critical-section state
- `[lpc17_40_can.c:lx_cpu_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[lpc17_40_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[lpc17_40_fpgainitialize.c:lx_cpu_fpga_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc17_40_fpgainitialize.c:lx_cpu_fpga_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_sdraminitialize.c:lx_cpu_sdram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc17_40_ssp.c:lx_cpu_sspdev_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_ulan.c:nuttx_ulan_get_chip_data]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh lx_cpu:nsh && make`
