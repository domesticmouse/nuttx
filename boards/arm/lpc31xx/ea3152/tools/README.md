# `ea3152/tools` Component (`boards/arm/lpc31xx/ea3152/tools`)

## Overview
Board support component `tools` for `ea3152` (`arm/lpc31xx`), containing 5 source/script file(s) (`crc32.c, lpchdr.c, lpchdr.h, mklpc.sh`).

## Interface
- `[lpchdr.h:crc32part]` Public declaration `crc32part()`
- `[lpchdr.h:crc32]` Public declaration `crc32()`
- `[lpchdr.h:lpc31_header_s]` Type definition `lpc31_header_s`
- `[crc32.c:crc32part]` Public function `crc32part()`
- `[crc32.c:crc32]` Public function `crc32()`
- `[lpchdr.c:main]` Public function `main()`
- `[mklpc.sh]` Shell script entry point `mklpc.sh`
- `[oocd.sh]` Shell script entry point `oocd.sh`

## Invariants
- `[mklpc.sh:exit]` Validates required environment variables, arguments, or files before execution
- `[oocd.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[mklpc.sh]` Executes shell commands on the host environment
- `[oocd.sh]` Invokes host utilities (`openocd`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh ea3152:ostest && make`
