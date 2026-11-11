# POSIX Regular Expressions (`libs/libc/regex`)

## Overview
Provides POSIX.2 regular expression compilation, matching, error formatting, and teardown (`<regex.h>`) based on the Ville Laurikari TRE tagged NFA (TNFA) engine.

## Interface
- `regcomp.c:regcomp` - Compiles a POSIX basic or extended regular expression string into an internal `tre_tnfa_t` automaton stored in `preg->__opaque`.
- `regcomp.c:regfree` - Frees all heap allocations associated with a compiled `regex_t` (`preg`).
- `regexec.c:regexec` - Matches a compiled `regex_t` against a null-terminated string (or `REG_STARTEND` bounded slice), dispatching to either the parallel TNFA matcher (`tre_tnfa_run_parallel`) or backtracking matcher (`tre_tnfa_run_backtrack` when `tnfa->have_backrefs` is set) and populating `pmatch[]`.
- `regerror.c:regerror` - Converts a `reg_errcode_t` error code from `regcomp` or `regexec` into a human-readable diagnostic string in `buf`.
- `tre-mem.c:tre_mem_new_impl`, `tre-mem.c:tre_mem_alloc_impl`, `tre-mem.c:tre_mem_destroy` - Arena block allocator (`__tre_mem_*`) used during AST construction and TNFA compilation.
- `tre.h:tre_tnfa_t`, `tre.h:tre_tnfa_transition_t`, `tre.h:tre_submatch_data_t`, `tre.h:tre_mem_t` - Internal TNFA state, transition, submatch tag, and arena allocator types.

## Invariants
- `regexec.c:regexec` requires a `preg` previously initialized by `regcomp.c:regcomp`; when `REG_STARTEND` is set in `eflags`, `pmatch[0].rm_so >= 0` and `pmatch[0].rm_eo >= pmatch[0].rm_so` must hold (otherwise `REG_NOMATCH` is returned).
- `regexec.c:tre_fill_pmatch` preserves the invariant that any submatch not contained within its parent submatch bounds has both `rm_so` and `rm_eo` reset to `-1`.

## Side Effects
- `regcomp.c:regcomp`, `regexec.c:regexec`, and `tre-mem.c:tre_mem_alloc_impl` allocate and free dynamic heap memory via `malloc`/`calloc`/`realloc`/`free` (`xmalloc`/`xcalloc`/`xfree`).
- `regcomp.c:regfree` releases all internal transition, tag, submatch, and state arrays attached to `preg`.

## Verification
- Run: `make test`
