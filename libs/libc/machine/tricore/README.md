# Infineon TriCore Machine Support (`libs/libc/machine/tricore`)

## Overview
Provides 32-bit hardware atomic operations for Infineon TriCore processors using the `swap.w` and `cmpswap.w` instructions.

## Interface
- `arch_atomic.c:__atomic_store_4`, `arch_atomic.c:atomic_store_4` - Atomically stores a 32-bit value using `tricore_atomic_swap`.
- `arch_atomic.c:__atomic_load_4`, `arch_atomic.c:atomic_load_4` - Atomically loads a 32-bit volatile value.
- `arch_atomic.c:__atomic_exchange_4`, `arch_atomic.c:atomic_exchange_4` - Atomically swaps a 32-bit value at `ptr`.
- `arch_atomic.c:__atomic_compare_exchange_4`, `arch_atomic.c:atomic_compare_exchange_4` - Atomically compares and swaps a 32-bit value using `tricore_atomic_cmpswap`, updating `*expect` on failure.
- `arch_atomic.c:__atomic_flags_test_and_set_4`, `arch_atomic.c:atomic_flags_test_and_set_4` - Atomically sets `*ptr` to `1` and returns the previous 32-bit value.
- `arch_atomic.c:__atomic_fetch_add_4`, `arch_atomic.c:atomic_fetch_add_4`, `arch_atomic.c:__atomic_fetch_sub_4`, `arch_atomic.c:atomic_fetch_sub_4`, `arch_atomic.c:__atomic_fetch_and_4`, `arch_atomic.c:atomic_fetch_and_4`, `arch_atomic.c:__atomic_fetch_or_4`, `arch_atomic.c:atomic_fetch_or_4`, `arch_atomic.c:__atomic_fetch_xor_4`, `arch_atomic.c:atomic_fetch_xor_4` - Atomic 32-bit read-modify-write operations implemented as `cmpswap.w` retry loops.

## Invariants
- `arch_atomic.c:tricore_atomic_swap` and `arch_atomic.c:tricore_atomic_cmpswap` require `ptr` to be a valid 32-bit aligned memory address supported by TriCore `swap.w`/`cmpswap.w` instructions.

## Side Effects
- Mutates the target 32-bit memory word pointed to by `ptr` (and `*expect` on compare-exchange mismatch) using hardware atomic bus transactions.

## Verification
- Run: `make test`
