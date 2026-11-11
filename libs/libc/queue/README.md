# Singly and Doubly Linked Queues (`libs/libc/queue`)

## Overview
Instantiates non-inlined out-of-line implementations of the NuttX singly-linked (`sq_queue_t`) and doubly-linked (`dq_queue_t`) queue manipulation functions from `<nuttx/queue.h>` when `CONFIG_LIBC_INLINE_QUEUE` is not enabled globally.

## Interface
- `queue.c:CONFIG_LIBC_INLINE_QUEUE`, `queue.c:STATIC_INLINE` - Defines `CONFIG_LIBC_INLINE_QUEUE` and an empty `STATIC_INLINE` macro before including `<nuttx/queue.h>` to emit external symbol definitions for `sq_*` and `dq_*` queue routines (`sq_addfirst`, `sq_addlast`, `sq_addafter`, `sq_rem`, `sq_remfirst`, `sq_remlast`, `sq_remafter`, `sq_count`, `dq_addfirst`, `dq_addlast`, `dq_addafter`, `dq_addbefore`, `dq_rem`, `dq_remfirst`, `dq_remlast`, `dq_count`, `dq_split`).

## Invariants
- Queue manipulation functions require valid `sq_queue_t` / `dq_queue_t` queue heads and non-aliasing node pointers; callers are responsible for synchronization across threads or interrupt handlers.

## Side Effects
- Mutates forward and backward link pointers (`flink`, `blink`, `head`, `tail`) in caller-supplied queue and entry structures in place.

## Verification
- Run: `make test`
