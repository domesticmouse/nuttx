# Hardware Spinlock Subsystem Headers (`include/nuttx/hwspinlock`)

## Overview
Defines the lower-half operations table and inline lock/unlock primitives for hardware spinlock peripherals used for inter-processor synchronization in heterogeneous or asymmetric multiprocessing (AMP/SMP) systems.

## Interface
- `hwspinlock.h:hwspinlock_ops_s`, `hwspinlock.h:hwspinlock_dev_s` - Hardware spinlock operation vtable (`trylock`, `relax`, `unlock`) and device descriptor (`id`, `priority`, `ops`).
- `hwspinlock.h:hwspin_trylock`, `hwspinlock.h:hwspin_trylock_irqsave`, `hwspinlock.h:hwspin_lock`, `hwspinlock.h:hwspin_lock_irqsave`, `hwspinlock.h:hwspin_unlock`, `hwspinlock.h:hwspin_unlock_restore` - Inline functions for acquiring and releasing hardware spinlocks with optional local interrupt masking (`up_irq_save` / `up_irq_restore`).

## Invariants
- `hwspinlock.h:hwspinlock_dev_s` must have non-null `ops->trylock` and `ops->unlock` function pointers (`ops->relax` is optional and checked before invocation).
- Callers of `hwspinlock.h:hwspin_lock_irqsave` (or successful `hwspin_trylock_irqsave`) must release the lock with `hwspin_unlock_restore` passing the saved `irqstate_t` flags.

## Side Effects
- `hwspinlock.h:hwspin_lock_irqsave` and `hwspinlock.h:hwspin_trylock_irqsave` disable local CPU interrupts via `up_irq_save()` while acquiring the hardware lock register.
- `hwspinlock.h:hwspin_trylock`, `hwspinlock.h:hwspin_lock`, and `hwspinlock.h:hwspin_unlock` perform atomic MMIO reads/writes to hardware spinlock peripheral registers shared across processors.

## Verification
- Run: `make test`
