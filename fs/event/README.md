# Named Kernel Event Groups (EventFS)

## Overview
Provides VFS-backed named event group management, allowing tasks to open, create, share, and close named `nxevent_t` synchronization objects registered as pseudo-filesystem inodes under `CONFIG_FS_NAMED_EVENTS_VFS_PATH`.

## Interface
- `event_open.c:nxevent_open` - Opens or creates a named event group inode and returns a pointer to its `nxevent_t` instance.
- `event_close.c:nxevent_close` - Decrements the reference count on a named event group inode and destroys/frees it when the count reaches zero.
- `event.h:MAX_EVENTPATH` - Maximum path buffer length for named event group VFS paths.

## Invariants
- Inodes matched by `event_open.c:nxevent_open` must carry the `INODE_IS_NAMEDEVENT` type flag; mismatches return `-ENXIO`.
- `event_close.c:nxevent_close` must only destroy `ne_event` and free the inode when `atomic_sub(&inode->i_crefs, 1) <= 1` and the inode has been unlinked (`inode->i_peer == NULL`).

## Side Effects
- Acquires and releases the global inode tree lock (`inode_lock`/`inode_unlock`) when reserving new named event inodes (`event_open.c:nxevent_open`).
- Allocates and frees `struct nevent_inode_s` memory via `group_malloc` and `group_free`, and triggers `notify_open`/`notify_close2` events when `CONFIG_FS_NOTIFY` is enabled.

## Verification
- Run: `make test`
