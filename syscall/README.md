# NuttX System Call Lookup Tables (`syscall`)

## Overview
System call table specification (`syscall.csv`), system call function name lookup array (`syscall_names.c`), and kernel-side system call stub function pointer table (`syscall_stublookup.c`).

## Interface
- `[syscall_names.c:g_funcnames]`
- `[syscall_stublookup.c:g_stublookup]`

## Invariants
- `[syscall_names.c:g_funcnames]` and `[syscall_stublookup.c:g_stublookup]` are indexed by syscall number up to `SYS_nsyscalls` generated from `<sys/syscall_lookup.h>` and `[syscall.csv]`.
- `[syscall_stublookup.c:CONFIG_LIB_SYSCALL]` compiles `g_stublookup` only when `CONFIG_LIB_SYSCALL` is defined.

## Side Effects
- None

## Verification
- Run: `make test`
