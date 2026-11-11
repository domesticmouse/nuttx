# `imxrt1180-evk/tools` Component (`boards/arm/imxrt/imxrt1180-evk/tools`)

## Overview
Board support component `tools` for `imxrt1180-evk` (`arm/imxrt`), containing 2 source/script file(s) (`flash-jlink.sh, gdbserver-jlink.sh`).

## Interface
- `[flash-jlink.sh]` Shell script entry point `flash-jlink.sh`
- `[gdbserver-jlink.sh]` Shell script entry point `gdbserver-jlink.sh`

## Invariants
- `[flash-jlink.sh:exit]` Validates required environment variables, arguments, or files before execution
- `[gdbserver-jlink.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[flash-jlink.sh]` Invokes host utilities (`JLinkExe`, `cp`, `rm`) to flash, debug, or test firmware
- `[gdbserver-jlink.sh]` Invokes host utilities (`JLinkGDBServer`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh imxrt1180-evk:nsh && make`
