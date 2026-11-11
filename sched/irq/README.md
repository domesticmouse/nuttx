# irq

## Overview
Manages the hardware and software interrupt vector table (`g_irqvector`), interrupt dispatch, shared IRQ chains (`CONFIG_IRQCHAIN`), threaded and workqueue-deferred interrupts, UP/SMP critical sections (`enter_critical_section` / `leave_critical_section`), and `/proc/irqs` statistics (`CONFIG_FS_PROCFS`).

## Interface
- `irq.h:g_irqvector` (`irq_initialize.c:g_irqvector`) - Global table of registered `struct irq_info_s` handlers indexed by mapped IRQ slot (`NR_IRQS` or `CONFIG_ARCH_NUSER_INTERRUPTS`).
- `irq.h:g_cpu_irqlock` (`irq_csection.c:g_cpu_irqlock`, `CONFIG_SMP`) - Global spinlock (`rspinlock_t`) serializing SMP critical sections.
- `irq.h:g_cpu_irqset` (`irq_csection.c:g_cpu_irqset`, `CONFIG_SMP`) - Bitset (`cpu_set_t`) of CPUs currently inside a critical section.
- `irq.h:g_cpu_nestcount` (`irq_csection.c:g_cpu_nestcount`, `CONFIG_SMP`) - Per-CPU nesting counter for interrupt-context critical sections.
- `irq.h:irq_initialize` (`irq_initialize.c:irq_initialize`) - Initializes all entries in `irq_initialize.c:g_irqvector` to `irq_unexpectedisr.c:irq_unexpected_isr` and initializes the IRQ chain pool.
- `irq.h:irq_unexpected_isr` (`irq_unexpectedisr.c:irq_unexpected_isr`) - Default handler for unassigned interrupts; logs an error and triggers `PANIC()`.
- `irq.h:irq_foreach` (`irq_foreach.c:irq_foreach`) - Iterates over all active entries in `irq_initialize.c:g_irqvector` under a critical section.
- `irq.h:irqchain_initialize` / `irq.h:is_irqchain` / `irq.h:irqchain_attach` / `irq_chain.c:irqchain_detach` (`CONFIG_IRQCHAIN`) - Manages chained multiple ISR handlers sharing a single IRQ line.
- `irq_attach.c:irq_attach` / `irq_attach.c:irq_to_ndx` / `irq_attach.c:ndx_to_irq` - Attaches or detaches an interrupt handler in `irq_initialize.c:g_irqvector` and translates IRQ numbers to table indices.
- `irq_attach_thread.c:irq_attach_thread` - Attaches a top-half ISR and spawns a dedicated high-priority kernel thread for the bottom-half `isrthread`.
- `irq_attach_wqueue.c:irq_attach_wqueue` - Attaches a top-half ISR and schedules bottom-half `isrwq` execution on a high-priority work queue.
- `irq_dispatch.c:irq_dispatch` - Architecture entry point that invokes the registered ISR for `irq`, records statistics, and performs stack/heap checks.
- `irq_csection.c:enter_critical_section` / `irq_csection.c:enter_critical_section_notrace` / `irq_csection.c:leave_critical_section` / `irq_csection.c:leave_critical_section_notrace` - Enters and leaves nestable UP/SMP critical sections.
- `irq_procfs.c:g_irq_operations` (`CONFIG_FS_PROCFS`) - `struct procfs_operations` table implementing `/proc/irqs`.

## Invariants
- Every slot in `irq_initialize.c:g_irqvector` points to a valid function (`irq_unexpectedisr.c:irq_unexpected_isr` when detached, never `NULL`) once `irq_initialize.c:irq_initialize` has run.
- In `irq_csection.c:enter_critical_section_notrace`, local interrupts are disabled (`up_irq_save`) prior to acquiring `irq_csection.c:g_cpu_irqlock`, and `rtcb->irqcount` (`< INT16_MAX`) or `g_cpu_nestcount[cpu]` (`< UINT8_MAX`) tracks nesting depth without overflow.

## Side Effects
- Enables and disables hardware interrupt lines (`up_enable_irq`, `up_disable_irq`), spawns ISR threads/workqueues (`kthread_create`, `work_queue_create`), and allocates IRQ chain nodes from `irq_chain.c:g_irqchainpool` or `kmm_malloc`.
- Feeds interrupt timing jitter to the entropy pool (`add_irq_randomness`), checks kernel heap integrity (`kmm_checkcorruption`), checks interrupt stack watermarks (`up_check_intstack`), emits scheduler notes (`sched_note_irqhandler`), and panics via `CRITMONITOR_PANIC` if ISR execution exceeds `CONFIG_SCHED_CRITMONITOR_MAXTIME_IRQ` in `irq_dispatch.c:irq_dispatch`.
- Invokes `PANIC()` when an unregistered interrupt fires in `irq_unexpectedisr.c:irq_unexpected_isr`.

## Verification
- Run: `make test`
