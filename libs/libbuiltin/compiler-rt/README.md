# compiler-rt

## Overview
Provides LLVM `compiler-rt` instrumentation profiling and code coverage runtime support for NuttX, including raw profile serialization (`__llvm_profile_dump`), memory/file GCOV-compatible dump wrappers, and platform section boundary accessors for `__llvm_prf_data`, `__llvm_prf_names`, and `__llvm_prf_cnts`.

## Interface
- `InstrProfilingPlatform.c:__llvm_profile_register_function`, `InstrProfilingPlatform.c:__llvm_profile_register_names_function`, `InstrProfilingPlatform.c:__llvm_profile_begin_data`, `InstrProfilingPlatform.c:__llvm_profile_end_data`, `InstrProfilingPlatform.c:__llvm_profile_begin_names`, `InstrProfilingPlatform.c:__llvm_profile_end_names`, `InstrProfilingPlatform.c:__llvm_profile_begin_counters`, `InstrProfilingPlatform.c:__llvm_profile_end_counters`, `InstrProfilingPlatform.c:__llvm_profile_begin_bitmap`, `InstrProfilingPlatform.c:__llvm_profile_end_bitmap`, `InstrProfilingPlatform.c:__llvm_profile_begin_orderfile`, `InstrProfilingPlatform.c:__llvm_profile_begin_vnodes`, `InstrProfilingPlatform.c:__llvm_profile_end_vnodes`, `InstrProfilingPlatform.c:__llvm_write_binary_ids`, `InstrProfilingPlatform.c:CurrentVNode`, `InstrProfilingPlatform.c:EndVNode`
- `coverage.c:__llvm_profile_get_num_data`, `coverage.c:__llvm_profile_register_function`, `coverage.c:__llvm_profile_register_names_function`, `coverage.c:__llvm_profile_dump`, `coverage.c:__gcov_dump`, `coverage.c:__gcov_dump_to_memory`, `coverage.c:__gcov_reset`, `coverage.c:__llvm_profile_runtime`

## Invariants
- Linker-provided section symbols (`coverage.c:__start__llvm_prf_data`, `coverage.c:__end__llvm_prf_data`, `coverage.c:__start__llvm_prf_names`, `coverage.c:__end__llvm_prf_names`, `coverage.c:__start__llvm_prf_cnts`, `coverage.c:__end__llvm_prf_cnts`) must bound contiguous profile records in memory, with `__llvm_profile_data` aligned to 8 bytes (`coverage.c:__llvm_profile_data`) and name sections padded to 8-byte alignment (`coverage.c:__llvm_profile_get_num_padding_bytes`).
- `coverage.c:__gcov_dump` requires the `GCOV_PREFIX` environment variable to be set to a valid file path before writing profile output.

## Side Effects
- `coverage.c:__llvm_profile_dump` writes raw LLVM profile headers, data, counters, and names to a `struct lib_outstream_s` stream.
- `coverage.c:__gcov_dump` reads `GCOV_PREFIX` via `getenv` and opens/truncates/writes the target file via `_NX_OPEN` and `_NX_CLOSE`, mutating errno on failure via `_NX_SETERRNO`.
- `coverage.c:__gcov_dump_to_memory` writes serialized profile data into caller-supplied memory via `lib_memoutstream`.

## Verification
- Run: `make test`
