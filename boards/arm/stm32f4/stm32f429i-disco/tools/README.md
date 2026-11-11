# `stm32f429i-disco/tools` Component (`boards/arm/stm32f4/stm32f429i-disco/tools`)

## Overview
Board support component `tools` for `stm32f429i-disco` (`arm/stm32f4`), containing 1 source/script file(s) (`fbcalc.sh`).

## Interface
- `[fbcalc.sh]` Shell script entry point `fbcalc.sh`

## Invariants
- `[fbcalc.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[fbcalc.sh]` Executes shell commands on the host environment

## Verification
- Run: `./tools/configure.sh stm32f429i-disco:nsh && make`
