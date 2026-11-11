# BCM2711 (Raspberry Pi 4B) Boot & Post-Build Tools

## Overview
Provides boot firmware download scripts and post-build Makefile rules for the Broadcom BCM2711 SoC on the Raspberry Pi 4B board.

## Interface
- `bootfiles.sh` - Shell script that downloads official Raspberry Pi 4B device tree and GPU firmware boot files (`bcm2711-rpi-4-b.dtb`, `fixup4*.dat`, `start4*.elf`) from the Raspberry Pi firmware repository.
- `Config.mk:POSTBUILD`, `Config.mk:CONFIG_TXT` - Makefile post-build macro enabled when `CONFIG_ARCH_BOARD_RASPBERRYPI_4B=y` that generates the Raspberry Pi boot `config.txt` file pointing to `kernel=nuttx.bin`.

## Invariants
- `Config.mk:POSTBUILD` is only defined when `CONFIG_ARCH_BOARD_RASPBERRYPI_4B` is set to `y` and always sets `arm_64bit=1` and `core_freq_min=500` in `config.txt` (appending `uart_2ndstage=1` if `CONFIG_RPI4B_DEBUG_BOOT` is enabled).

## Side Effects
- `bootfiles.sh` performs network requests via `curl -O -L` to `raw.githubusercontent.com/raspberrypi/firmware` and writes `bcm2711-rpi-4-b.dtb`, `fixup4*.dat`, and `start4*.elf` into the current working directory.
- `Config.mk:POSTBUILD` creates or overwrites `config.txt` in the build directory.

## Verification
- Run: `make test`
