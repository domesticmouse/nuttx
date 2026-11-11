# `lpc4357-evb/scripts` Component (`boards/arm/lpc43xx/lpc4357-evb/scripts`)

## Overview
Board support component `scripts` for `lpc4357-evb` (`arm/lpc43xx`), containing 2 source/script file(s) (`bin_checksum_hex.sh, flash.sh`).

## Interface
- `[bin_checksum_hex.sh]` Shell script entry point `bin_checksum_hex.sh`
- `[flash.sh]` Shell script entry point `flash.sh`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_LPC43_BOOT_CS0FLASH`, `CONFIG_LPC43_BOOT_FLASHA`, `CONFIG_LPC43_BOOT_FLASHB`, `CONFIG_LPC43_BOOT_SPIFI`, `CONFIG_LPC43_BOOT_SRAM`
- `[flash.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[bin_checksum_hex.sh]` Executes shell commands on the host environment
- `[flash.sh]` Invokes host utilities (`mv`, `rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh lpc4357-evb:nsh && make`
