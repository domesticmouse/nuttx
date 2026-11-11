# Audio Pipeline Buffer Management (`libs/libc/audio`)

## Overview
Provides allocation, reference counting, and deallocation routines for Audio Pipeline Buffers (`struct ap_buffer_s`) when `CONFIG_AUDIO` is enabled. These buffers encapsulate audio sample payloads and synchronization locks passed between user-space audio components and audio device drivers.

## Interface
- `[lib_buffer.c:apb_alloc]` - Allocates and initializes a reference-counted `struct ap_buffer_s` and its embedded sample payload according to `struct audio_buf_desc_s`.
- `[lib_buffer.c:apb_reference]` - Atomically increments the reference count (`crefs`) of an active `struct ap_buffer_s`.
- `[lib_buffer.c:apb_free]` - Atomically decrements the reference count (`crefs`) of an `ap_buffer_s` and destroys its mutex and frees its heap memory once `crefs` reaches zero.

## Invariants
- `bufdesc->u.pbuffer` passed to `[lib_buffer.c:apb_alloc]` must be non-NULL (`DEBUGASSERT(bufdesc->u.pbuffer != NULL)`).
- `apb` passed to `[lib_buffer.c:apb_reference]` and `[lib_buffer.c:apb_free]` must be non-NULL (`DEBUGASSERT(apb != NULL)`).
- `[lib_buffer.c:apb_alloc]` initializes `apb->crefs` to `1`; every subsequent `[lib_buffer.c:apb_reference]` must be balanced by `[lib_buffer.c:apb_free]`.

## Side Effects
- `[lib_buffer.c:apb_alloc]` allocates user-space heap memory via `lib_umalloc()`, initializes the recursive/mutex lock via `nxmutex_init(&apb->lock)`, and writes the resulting buffer pointer to `*bufdesc->u.pbuffer`.
- `[lib_buffer.c:apb_reference]` and `[lib_buffer.c:apb_free]` acquire and release `apb->lock` via `nxmutex_lock()` and `nxmutex_unlock()`.
- `[lib_buffer.c:apb_free]` destroys `apb->lock` via `nxmutex_destroy()` and releases memory via `lib_ufree()` when the reference count drops to zero.

## Verification
- Run: `make test`
