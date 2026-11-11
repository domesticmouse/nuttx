# nxgdb Type Protocols

## Overview
Provides Python `typing.Protocol` definitions modeling GDB values (`gdb.Value`) and core NuttX C kernel structures for static type checking across the `nxgdb` debugging package. These classes mirror kernel structs for circular buffers, filesystems, interrupts, memory management, threads/tasks, uORB sensors, watchdogs, and work queues.

## Interface
- `value.py:Value` - Base `typing.Protocol` wrapping `gdb.Value` methods (`cast`, `dereference`, `referenced_value`, `reference_value`, `rvalue_reference_value`, `const_value`, `dynamic_cast`, `reinterpret_cast`, `format_string`, `string`) and attributes (`address`, `is_optimized_out`, `type`, `dynamic_type`, `is_lazy`, `bytes`).
- `circbuf.py:CircBuf` - Protocol representing `struct circbuf_s`.
- `fs.py:Fd`, `fs.py:File`, `fs.py:Inode`, `fs.py:FdList` - Protocols representing `struct fd`, `struct file`, `struct inode`, and `struct fdlist`.
- `irq.py:IRQInfo` - Protocol representing `struct irq_info_s`.
- `mm.py:ProcfsMeminfoEntry`, `mm.py:MMAllocNode`, `mm.py:MMFreeNode`, `mm.py:MMHeap`, `mm.py:MemPool`, `mm.py:MemPoolMultiple`, `mm.py:MemPoolBlock` - Protocols representing NuttX heap and memory pool structures (`struct procfs_meminfo_entry_s`, `struct mm_allocnode_s`, `struct mm_freenode_s`, `struct mm_heap_s`, `struct mempool_s`, `struct mempool_multiple_s`, `struct mempool_backtrace_s`).
- `thread.py:Group`, `thread.py:Tcb` - Protocols representing task groups (`struct group_s`) and task control blocks (`struct tcb_s`).
- `uorb.py:OrbMetadata`, `uorb.py:SensorMeta`, `uorb.py:SensorState`, `uorb.py:SensorUState`, `uorb.py:SensorUpper`, `uorb.py:SensorLower`, `uorb.py:SensorUser` - Protocols representing uORB metadata and sensor driver structures (`struct orb_metadata_s`, `struct sensor_meta_s`, `struct sensor_state_s`, `struct sensor_ustate_s`, `struct sensor_upperhalf_s`, `struct sensor_lowerhalf_s`, `struct sensor_user_s`).
- `wdog.py:WDog` - Protocol representing watchdog timer structure `struct wdog_s`.
- `wqueue.py:Work`, `wqueue.py:KWorker`, `wqueue.py:KWorkQueue`, `wqueue.py:HPWorkQueue`, `wqueue.py:LPWorkQueue` - Protocols representing kernel work items and work queues (`struct work_s`, `struct kworker_s`, `struct kwork_wqueue_s`, `struct hp_wqueue_s`, `struct lp_wqueue_s`).

## Invariants
- Protocol field names and types in `circbuf.py:CircBuf`, `fs.py:Fd`, `fs.py:File`, `fs.py:Inode`, `fs.py:FdList`, `irq.py:IRQInfo`, `mm.py:MMHeap`, `thread.py:Group`, `thread.py:Tcb`, `uorb.py:SensorUpper`, `wdog.py:WDog`, and `wqueue.py:KWorkQueue` must stay synchronized with their corresponding C structure definitions in the NuttX kernel headers.
- All structure protocols inherit from `value.py:Value` and are intended for static type annotations and IDE completion rather than runtime instantiation.

## Side Effects
- None

## Verification
- Run: `make test`
