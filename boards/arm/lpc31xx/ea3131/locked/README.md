# `ea3131/locked` Component (`boards/arm/lpc31xx/ea3131/locked`)

## Overview
Board support component `locked` for `ea3131` (`arm/lpc31xx`), containing 1 source/script file(s) (`mklocked.sh`).

## Interface
- `[mklocked.sh]` Shell script entry point `mklocked.sh`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`
- `[mklocked.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[mklocked.sh]` Invokes host utilities (`rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh ea3131:nsh && make`
