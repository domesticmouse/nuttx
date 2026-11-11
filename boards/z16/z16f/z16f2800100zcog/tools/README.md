# `z16f2800100zcog/tools` Component (`boards/z16/z16f/z16f2800100zcog/tools`)

## Overview
Board support component `tools` for `z16f2800100zcog` (`z16/z16f`), containing 1 source/script file(s) (`dopatch.sh`).

## Interface
- `[dopatch.sh]` Shell script entry point `dopatch.sh`

## Invariants
- `[dopatch.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[dopatch.sh]` Executes shell commands on the host environment

## Verification
- Run: `./tools/configure.sh z16f2800100zcog:nsh && make`
