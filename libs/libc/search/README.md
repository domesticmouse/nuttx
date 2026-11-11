# Search Tables, Trees & Queues (`libs/libc/search`)

## Overview
Implements POSIX `<search.h>` data structures and algorithms, including hash tables (`hcreate`/`hsearch`), height-balanced AVL binary search trees (`tsearch`/`tfind`/`tdelete`/`twalk`/`tdestroy`), linear array search (`lsearch`/`lfind`), and circular/doubly-linked element queues (`insque`/`remque`).

## Interface
- `hash_func.c:__default_hash` - Default Chris Torek `* 33` string hash function.
- `hcreate.c:hcreate`, `hcreate.c:hdestroy`, `hcreate.c:hsearch`, `hcreate.c:hforeach` - Process-global hash table lifecycle, lookup/insertion, and iteration functions wrapping `hcreate_r`/`hdestroy_r`/`hsearch_r`/`hforeach_r`.
- `hcreate_r.c:hcreate_r`, `hcreate_r.c:hdestroy_r`, `hcreate_r.c:hsearch_r`, `hcreate_r.c:hforeach_r` - Reentrant chaining hash table implementation operating on `struct hsearch_data`.
- `lib_insque.c:insque`, `lib_insque.c:remque` - Inserts or removes an element in a doubly-linked or circular list (`struct qelem_s`).
- `lib_lsearch.c:lfind`, `lib_lsearch.c:lsearch` - Linear search (`lfind`) and search-or-append (`lsearch`) over a contiguous array of `*nelp` elements of size `width`.
- `tsearch.h:struct tnode_s`, `tsearch.h:tsearch_balance` - Internal AVL binary search tree node representation and height-rebalancing routine.
- `lib_tsearch.c:tsearch`, `lib_tsearch.c:tsearch_balance` - Searches for `key` in an AVL binary tree `*rootp`, inserting a newly allocated node and rebalancing if absent.
- `lib_tfind.c:tfind` - Searches for `key` in binary tree `*rootp` without modifying the tree.
- `lib_tdelete.c:tdelete` - Deletes the node matching `key` from `*rootp`, rebalancing the tree and returning the parent pointer.
- `lib_twalk.c:twalk` - Performs a depth-first traversal (`preorder`, `postorder`, `endorder`, `leaf`) of binary tree `root`.
- `lib_tdestroy.c:tdestroy` - Post-order frees all nodes in binary tree `root` and invokes `free_node` on each datum.

## Invariants
- `lib_tsearch.c:tsearch_balance` maintains the AVL balance invariant (`|height(left) - height(right)| <= 1`) and node height cache after every `tsearch` insertion and `tdelete` removal.
- `hcreate_r.c:hcreate_r` requires `htab->table == NULL` on entry (returning `0` with `errno = EINVAL` if already initialized) and rounds bucket count to a power of two within `[MIN_BUCKETS, MAX_BUCKETS]`.

## Side Effects
- `hcreate_r.c:hcreate_r`, `hcreate_r.c:hsearch_r`, `hcreate_r.c:hdestroy_r`, `lib_tsearch.c:tsearch`, `lib_tdelete.c:tdelete`, and `lib_tdestroy.c:tdestroy` allocate and free nodes/buckets on the heap via `lib_malloc`, `lib_calloc`, and `lib_free`, and set `errno` (`ENOMEM`, `ESRCH`, `EINVAL`) on failure.
- `hcreate.c` mutates the module-static `g_htab` hash table instance.
- `lib_lsearch.c:lsearch` appends a new element to `base` and increments `*nelp` when `key` is not found.

## Verification
- Run: `make test`
