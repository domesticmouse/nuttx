# Object Stack Memory Allocator (`libs/libc/obstack`)

## Overview
Implements the GNU-compatible `<obstack.h>` object stack allocator (`struct obstack`) in `libc`. Obstacks manage LIFO region-based heap allocations in power-of-two-rounded chunks (`struct _obstack_chunk`), supporting both fixed-size allocations (`obstack_alloc`, `obstack_copy`) and incremental object growth (`obstack_grow`, `obstack_1grow`, `obstack_printf`, `obstack_finish`) with bulk deallocation back to any earlier object mark (`obstack_free`).

## Interface
- `[lib_obstack_init.c:obstack_init]` - Initializes an `obstack` handle with default `BUFSIZ` chunk size and empty chunk pointers.
- `[lib_obstack_alloc.c:obstack_alloc]` - Allocates an uninitialized object of `size` bytes on `h` and finishes it immediately.
- `[lib_obstack_copy.c:obstack_copy]`, `[lib_obstack_copy.c:obstack_copy0]` - Allocates and copies `size` bytes from `address` into a finished object (with `obstack_copy0` appending a trailing `'\0'`).
- `[lib_obstack_blank.c:obstack_blank]` - Grows the current unfinished object by `size` uninitialized bytes.
- `[lib_obstack_grow.c:obstack_grow]`, `[lib_obstack_grow.c:obstack_grow0]`, `[lib_obstack_grow.c:obstack_1grow]`, `[lib_obstack_grow.c:obstack_ptr_grow]`, `[lib_obstack_grow.c:obstack_int_grow]` - Appends arbitrary bytes, null-terminated data, a single character, a `void *` pointer, or an `int` to the currently growing object.
- `[lib_obstack_printf.c:obstack_printf]`, `[lib_obstack_vprintf.c:obstack_vprintf]` - Formats a `printf`-style string and appends it to the currently growing object on `h`.
- `[lib_obstack_finish.c:obstack_finish]`, `[lib_obstack_finish.c:obstack_finish_norealloc]` - Finalizes the currently growing object, returning its permanent base address (`object_base`) and advancing `object_base` to `next_free`.
- `[lib_obstack_free.c:obstack_free]` - Frees `object` and all objects allocated on `h` more recently than `object` (or frees all chunks when `object == NULL`).
- `[lib_obstack_make_room.c:obstack_make_room]` - Ensures at least `size` bytes of free room exist in the active chunk, allocating or reallocating a power-of-two chunk if needed.
- `[lib_obstack_room.c:obstack_room]`, `[lib_obstack_object_size.c:obstack_object_size]` - Returns the remaining free bytes in the active chunk or the current byte size of the growing object.
- `[lib_obstack_malloc.c:lib_obstack_malloc]`, `[lib_obstack_malloc.c:lib_obstack_realloc]` - Internal chunk allocation helpers that invoke `obstack_alloc_failed_handler()` if heap allocation fails.

## Invariants
- `h` passed to `[lib_obstack_init.c:obstack_init]`, `[lib_obstack_make_room.c:obstack_make_room]`, and `[lib_obstack_room.c:obstack_room]` must be non-NULL (`DEBUGASSERT(h)`), and `h->chunk_size` must be `> 0`.
- While an object is growing (`object_base != next_free`), its base address may move if `[lib_obstack_make_room.c:obstack_make_room]` allocates or reallocates a chunk; the object address is only stable after `[lib_obstack_finish.c:obstack_finish]`.

## Side Effects
- `[lib_obstack_make_room.c:obstack_make_room]` and `[lib_obstack_finish.c:obstack_finish]` allocate, reallocate, and free `_obstack_chunk` blocks via `lib_malloc()`, `lib_realloc()`, and `lib_free()`.
- `[lib_obstack_malloc.c:lib_obstack_malloc]` and `[lib_obstack_malloc.c:lib_obstack_realloc]` invoke `obstack_alloc_failed_handler()` (which calls `exit(EXIT_FAILURE)`) on out-of-memory errors.

## Verification
- Run: `make test`
