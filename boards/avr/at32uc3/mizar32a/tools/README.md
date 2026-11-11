# `mizar32a/tools` Component (`boards/avr/at32uc3/mizar32a/tools`)

## Overview
Board support component `tools` for `mizar32a` (`avr/at32uc3`), containing 1 source/script file(s) (`doisp.sh`).

## Interface
- `[doisp.sh]` Shell script entry point `doisp.sh`

## Invariants
- `[doisp.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[doisp.sh]` Invokes host utilities (`mv`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh mizar32a:nsh && make`
