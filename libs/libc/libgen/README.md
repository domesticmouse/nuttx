# Pathname Manipulation Routines (`libs/libc/libgen`)

## Overview
Implements the POSIX `<libgen.h>` pathname component extraction functions `basename()` and `dirname()`, splitting null-terminated filesystem path strings into their trailing filename and parent directory components.

## Interface
- `[lib_basename.c:basename]` - Strips trailing `'/'` characters from `path` and returns a pointer to the final pathname component.
- `[lib_dirname.c:dirname]` - Strips the trailing filename component from `path` and returns a pointer to the parent directory pathname.

## Invariants
- Both `[lib_basename.c:basename]` and `[lib_dirname.c:dirname]` return `"."` when `path` is `NULL`, `""`, or (for `dirname`) contains no `'/'` characters, and return `"/"` when `path` consists solely of `'/'` characters.

## Side Effects
- `[lib_basename.c:basename]` and `[lib_dirname.c:dirname]` mutate the caller-supplied `path` buffer in-place by overwriting trailing or separator `'/'` characters with `'\0'`.

## Verification
- Run: `make test`
