# Power Management (PM) Subsystem (`drivers/power/pm`)

## Overview
Implements the system-wide Power Management (PM) framework in NuttX, including power domains, peripheral driver prepare/notify callbacks, wakelocks, runtime PM, idle-loop integration, `/proc/pm` statistics, and pluggable state governors (activity, greedy, and stability).

## Interface
- `[pm_initialize.c:pm_initialize]`, `[pm_register.c:pm_domain_register]`, `[pm_unregister.c:pm_domain_unregister]` - Initializes the PM subsystem and registers/unregisters peripheral `struct pm_callback_s` handlers per power domain (`[pm.h:struct pm_domain_s]`).
- `[pm_activity.c:pm_activity]`, `[pm_activity.c:pm_stay]`, `[pm_activity.c:pm_relax]`, `[pm_activity.c:pm_staytimeout]`, `[pm_activity.c:pm_staycount]`, `[pm_activity.c:pm_wakelock_init]`, `[pm_activity.c:pm_wakelock_stay]`, `[pm_activity.c:pm_wakelock_relax]`, `[pm_activity.c:pm_wakelock_staytimeout]` - Reports peripheral activity and acquires/releases domain wakelocks.
- `[pm_changestate.c:pm_changestate]`, `[pm_changestate.c:pm_updatestate]`, `[pm_changestate.c:pm_querystate]`, `[pm_checkstate.c:pm_checkstate]`, `[pm_autoupdate.c:pm_auto_updatestate]` - Queries recommended power states from the active governor and transitions domains between `PM_NORMAL`, `PM_IDLE`, `PM_STANDBY`, `PM_SLEEP`, and `PM_RESTORE`.
- `[pm_idle.c:pm_idle]`, `[pm_idle.c:pm_idle_lock]`, `[pm_idle.c:pm_idle_unlock]`, `[pm_lock.c:pm_domain_lock]`, `[pm_lock.c:pm_domain_unlock]` - CPU/SMP idle-loop power state coordination and domain locking.
- `[pm_runtime.c:pm_runtime_init]`, `[pm_runtime.c:pm_runtime_get]`, `[pm_runtime.c:pm_runtime_put]`, `[pm_runtime.c:pm_runtime_put_autosuspend]`, `[pm_runtime.c:pm_runtime_set_autosuspend_delay]` - Reference-counted device runtime power management.
- `[pm_governor.c:pm_set_governor]`, `[activity_governor.c:pm_activity_governor_initialize]`, `[greedy_governor.c:pm_greedy_governor_initialize]`, `[stability_governor.c:pm_stability_governor_initialize]` - Pluggable PM governor selection and built-in governors.

## Invariants
- Domain indices must satisfy `0 <= domain < CONFIG_PM_NDOMAINS` (`DEBUGASSERT`), and domain state transitions must hold the per-domain spinlock (`[pm_changestate.c:spin_lock_irqsave]`).
- If any registered driver's `prepare` callback returns a non-zero error during `[pm_changestate.c:pm_changestate]`, the transition is aborted and previously prepared drivers are rolled back.

## Side Effects
- Invokes registered driver `prepare` and `notify` callbacks across power domains, schedules timer/workqueue callbacks (`[pm_autoupdate.c:work_queue]`, `[pm_runtime.c:work_queue]`), and exposes `/proc/pm` statistics (`[pm_procfs.c:CONFIG_PM_NDOMAINS]`).

## Verification
- Run: `make test`
