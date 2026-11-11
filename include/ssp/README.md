# Stack Smashing Protector Header (`include/ssp`)

## Overview
Provides compiler Stack Smashing Protector (`SSP`) support macros and the failure handler prototype (`__stack_chk_fail`) used when GCC/Clang `-fstack-protector*` instrumentation detects a corrupted stack canary.

## Interface
- `ssp.h:__stack_chk_fail` - No-return runtime trap function invoked by compiler-generated stack-canary epilogues upon buffer overflow detection.
- `ssp.h:__ssp_inline` - Compiler attribute macro forcing always-inline semantics on SSP wrapper functions.

## Invariants
- `ssp.h:__stack_chk_fail` is declared with `noreturn_function` and must never return to its caller because the caller's stack frame and return address are already compromised.

## Side Effects
- Invoking `ssp.h:__stack_chk_fail` triggers a fatal assertion/panic and halts or resets the offending task/system.

## Verification
- Run: `make test`
