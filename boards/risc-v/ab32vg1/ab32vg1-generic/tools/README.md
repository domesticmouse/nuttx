# `ab32vg1-generic/tools` Component (`boards/risc-v/ab32vg1/ab32vg1-generic/tools`)

## Overview
Board support component `tools` for `ab32vg1-generic` (`risc-v/ab32vg1`), containing 1 source/script file(s) (`ab32vg1_dl.c`).

## Interface
- `[ab32vg1_dl.c:main]` Public function `main()`
- [`target`](./target/README.md): Board support component `tools/target` for `ab32vg1-generic` (`risc-v/ab32vg1`), containing 6 source/script file(s) (`boot.c, spiflash.c, stub.c, stub.h`).

## Invariants
- `[ab32vg1_dl.c:main]` Validates preconditions and returns `-EIO`, `-EPROTO`, `-ETIMEDOUT` on failure

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ab32vg1-generic:nsh && make`
