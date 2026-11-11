# Runtime Assertions and Stack Smashing Protection (`libs/libc/assert`)

## Overview
Implements the C library runtime assertion failure entry point (`__assert`) and compiler stack-smashing protector (`-fstack-protector`) runtime callbacks (`__stack_chk_guard`, `__stack_chk_fail`).

## Interface
- `[lib_assert.c:__assert]` - User-facing assertion failure handler invoked by the `assert()` and `DEBUGASSERT()` macros; forwards the failing filename, line number, and assertion expression to `_assert()` and terminates via `abort()`.
- `[lib_stackchk.c:__stack_chk_guard]` - Global stack canary guard variable initialized for GCC/Clang stack-smashing protection.
- `[lib_stackchk.c:__stack_chk_fail]` - Compiler-invoked failure callback executed when a corrupted stack canary is detected upon function return.

## Invariants
- `[lib_assert.c:__assert]` and `[lib_stackchk.c:__stack_chk_fail]` are `noreturn` functions that never return control to the caller.

## Side Effects
- `[lib_assert.c:__assert]` invokes `_assert(filename, linenum, msg, NULL)` and terminates the offending task/process via `abort()`.
- `[lib_stackchk.c:__stack_chk_fail]` triggers an immediate kernel/system panic via `PANIC()`.

## Verification
- Run: `make test`
