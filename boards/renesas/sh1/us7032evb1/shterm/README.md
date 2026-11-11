# `us7032evb1/shterm` Component (`boards/renesas/sh1/us7032evb1/shterm`)

## Overview
Board support component `shterm` for `us7032evb1` (`renesas/sh1`), containing 1 source/script file(s) (`shterm.c`).

## Interface
- `[shterm.c:main]` Public function `main()`

## Invariants
- `[shterm.c:main]` Validates preconditions and returns `-EAGAIN` on failure

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh us7032evb1:nsh && make`
