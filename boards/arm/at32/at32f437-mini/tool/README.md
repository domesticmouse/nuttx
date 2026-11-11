# `at32f437-mini/tool` Component (`boards/arm/at32/at32f437-mini/tool`)

## Overview
Board support component `tool` for `at32f437-mini` (`arm/at32`), containing 1 source/script file(s) (`mkromfs.sh`).

## Interface
- `[mkromfs.sh]` Shell script entry point `mkromfs.sh`

## Invariants
- None

## Side Effects
- `[mkromfs.sh]` Invokes host utilities (`genromfs`, `cp`, `rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh at32f437-mini:nsh && make`
