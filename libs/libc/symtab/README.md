# Symbol Table Lookup & Sorting (`libs/libc/symtab`)

## Overview
Provides symbol table lookup by symbol name (`symtab_findbyname`), closest-address lookup by value (`symtab_findbyvalue`), in-place sorting (`symtab_sortbyname`), and global system symbol table (`g_allsyms`) queries used by the ELF/module loader and backtrace/profiler subsystems.

## Interface
- `symtab_findbyname.c:symtab_findbyname` - Searches `symtab` (`nsyms` entries) for `name` using binary search when `CONFIG_SYMTAB_ORDEREDBYNAME` is enabled or linear scan otherwise (stripping a leading `'_'` when `CONFIG_SYMTAB_DECORATED` is enabled).
- `symtab_findbyvalue.c:symtab_findbyvalue` - Finds the `struct symtab_s` entry whose `sym_value` is closest to, but not greater than, `value` using binary search (`CONFIG_SYMTAB_ORDEREDBYVALUE`) or linear scan.
- `symtab_sortbyname.c:symtab_sortbyname` - Sorts an array of `struct symtab_s` entries in ascending lexicographical `sym_name` order.
- `symtab_allsyms.c:allsyms_findbyname`, `symtab_allsyms.c:allsyms_findbyvalue` - Searches the global kernel/application symbol table (`g_allsyms`, `g_nallsyms`) by name or address, calculating symbol size in `*symsize`.

## Invariants
- `symtab_findbyname.c:symtab_findbyname` and `symtab_findbyvalue.c:symtab_findbyvalue` assert `DEBUGASSERT(nsyms == 0)` if `symtab == NULL`, and `symtab_findbyname` asserts `DEBUGASSERT(name != NULL)`.
- `symtab_sortbyname.c:symtab_sortbyname` asserts `DEBUGASSERT(symtab != NULL && nsyms != 0)`.

## Side Effects
- `symtab_sortbyname.c:symtab_sortbyname` reorders elements of `symtab[]` in place.

## Verification
- Run: `make test`
