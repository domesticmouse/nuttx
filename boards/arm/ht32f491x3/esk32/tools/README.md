# `esk32/tools` Component (`boards/arm/ht32f491x3/esk32/tools`)

## Overview
Board support component `tools` for `esk32` (`arm/ht32f491x3`), containing 2 source/script file(s) (`flash.py, flash.sh`).

## Interface
- `[flash.py:is_windows_host]` Python function `is_windows_host()`
- `[flash.py:is_wsl]` Python function `is_wsl()`
- `[flash.py:build_command]` Python function `build_command(argv)`
- `[flash.py:main]` Python function `main(argv)`
- `[flash.sh]` Shell script entry point `flash.sh`

## Invariants
- `[flash.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[flash.py]` Spawns external subprocesses
- `[flash.sh]` Invokes host utilities (`openocd`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh esk32:nsh && make`
