# UndefinedBehaviorSanitizer Runtime (`mm/ubsan`)

## Overview
Provides the kernel and userspace UndefinedBehaviorSanitizer (UBSAN) runtime handlers for NuttX. Compiler-emitted instrumentation calls into these ABI entry points on arithmetic overflow, invalid shifts, out-of-bounds array indexing, pointer misalignment, null pointer dereferences, unreachable code paths, and invalid type conversions. When `CONFIG_MM_UBSAN_DUMMY` is enabled, the handlers compile as no-ops (except `__ubsan_handle_builtin_unreachable`, which always panics); otherwise they decode type descriptors and source locations to emit diagnostic error logs.

## Interface
- `[ubsan.h:enum type_kind_e]` - Enumeration of UBSAN runtime type descriptor kinds (`TYPE_KIND_INT`, `TYPE_KIND_FLOAT`, `TYPE_UNKNOWN`)
- `[ubsan.h:struct type_descriptor]` - Compiler-generated type metadata descriptor containing `type_kind`, `type_info`, and `type_name`
- `[ubsan.h:struct source_location]` - Source file, line, and column metadata structure for UBSAN call sites
- `[ubsan.h:struct overflow_data]` - Metadata payload for arithmetic overflow handlers
- `[ubsan.h:struct type_mismatch_data]`, `[ubsan.h:struct type_mismatch_data_v1]`, `[ubsan.h:struct type_mismatch_data_common]` - Metadata structures for pointer alignment, nullness, and type-check failures
- `[ubsan.h:struct nonnull_arg_data]` - Metadata structure for nonnull argument attribute violations
- `[ubsan.h:struct out_of_bounds_data]` - Metadata structure for array bounds violations
- `[ubsan.h:struct shift_out_of_bounds_data]` - Metadata structure for invalid bit shift operations
- `[ubsan.h:struct invalid_value_data]` - Metadata structure for loading invalid enum or boolean values
- `[ubsan.h:struct alignment_assumption_data]` - Metadata structure for failed pointer alignment assumptions
- `[ubsan.c:__ubsan_handle_add_overflow]`, `[ubsan.c:__ubsan_handle_sub_overflow]`, `[ubsan.c:__ubsan_handle_mul_overflow]`, `[ubsan.c:__ubsan_handle_negate_overflow]`, `[ubsan.c:__ubsan_handle_divrem_overflow]` - Integer arithmetic overflow runtime traps
- `[ubsan.c:__ubsan_handle_pointer_overflow]` - Pointer arithmetic overflow runtime trap
- `[ubsan.c:__ubsan_handle_out_of_bounds]` - Array index out-of-bounds runtime trap
- `[ubsan.c:__ubsan_handle_shift_out_of_bounds]` - Shift exponent out-of-bounds or negative shift runtime trap
- `[ubsan.c:__ubsan_handle_type_mismatch]`, `[ubsan.c:__ubsan_handle_type_mismatch_v1]` - Null pointer, insufficient object size, and misaligned pointer runtime traps
- `[ubsan.c:__ubsan_handle_alignment_assumption]` - Alignment assumption failure runtime trap
- `[ubsan.c:__ubsan_handle_nonnull_arg]` - Null argument passed to nonnull-annotated parameter runtime trap
- `[ubsan.c:__ubsan_handle_load_invalid_value]` - Out-of-range boolean or enum load runtime trap
- `[ubsan.c:__ubsan_handle_invalid_builtin]` - Invalid builtin function argument runtime trap
- `[ubsan.c:__ubsan_handle_dynamic_type_cache_miss]` - Dynamic C++ type cache miss runtime trap
- `[ubsan.c:__ubsan_handle_builtin_unreachable]` - Unreachable code path trap that terminates execution via `PANIC()`

## Invariants
- Integer operands with bit width less than or equal to `sizeof(uintptr_t) * 8` (`[ubsan.c:is_inline_int]`) are encoded directly inside the `void *` value argument; wider integers (such as 64-bit integers on 32-bit targets) are passed by pointer reference (`[ubsan.c:get_signed_val]`, `[ubsan.c:get_unsigned_val]`).
- Reaching `[ubsan.c:__ubsan_handle_builtin_unreachable]` is a fatal invariant violation and never returns.

## Side Effects
- Emits formatted UBSAN diagnostic headers, operand values, and separator banners to the system log via `_alert` (`[ubsan.c:ubsan_prologue]`, `[ubsan.c:ubsan_epilogue]`).
- Invokes `PANIC()` unconditionally in `[ubsan.c:__ubsan_handle_builtin_unreachable]`.

## Verification
- Run: `make test`
