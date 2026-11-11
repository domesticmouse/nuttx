# `imx93-qsb/tools` Component (`boards/arm/imx9/imx93-qsb/tools`)

## Overview
Board support component `tools` for `imx93-qsb` (`arm/imx9`), containing 1 source/script file(s) (`enable_onboard_debug.py`).

## Interface
- `[enable_onboard_debug.py:set_bit]` Python function `set_bit(value, bit)`
- `[enable_onboard_debug.py:clear_bit]` Python function `clear_bit(value, bit)`
- `[enable_onboard_debug.py:read_modify_write]` Python function `read_modify_write(port, reg_addr, bit, set_high=True)`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imx93-qsb:nsh && make`
