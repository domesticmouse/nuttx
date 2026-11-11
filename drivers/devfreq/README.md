# Device Frequency Scaling (Devfreq) Framework (`drivers/devfreq`)

## Overview
Implements the NuttX dynamic device frequency scaling (`devfreq`) subsystem, including governor registration and frequency re-evaluation, built-in governors (`ondemand`, `performance`, `powersave`), Quality-of-Service (QoS) min/max frequency constraints,notifier chains, and `procfs` inspection (`/proc/devfreq`).

## Interface
- `devfreq.c:devfreq_register`, `devfreq.c:devfreq_unregister`, `devfreq.c:devfreq_suspend`, `devfreq.c:devfreq_resume`, `devfreq.c:devfreq_get_frequency` - Registers/unregisters `devfreq_s` devices, suspends/resumes scaling, and updates target operating frequencies.
- `devfreq.c:devfreq_find_by_name`, `devfreq.c:devfreq_find_by_index`, `devfreq.c:devfreq_register_notifier`, `devfreq.c:devfreq_unregister_notifier` - Looks up registered devfreq instances and manages transition notifier callbacks.
- `devfreq.c:devfreq_qos_add_request`, `devfreq.c:devfreq_qos_update_request`, `devfreq.c:devfreq_qos_remove_request` - Adds, updates, and removes min/max frequency QoS requests on a `devfreq_s` device.
- `devfreq_qos.c:qos_constraints_init`, `devfreq_qos.c:qos_add_request`, `devfreq_qos.c:qos_update_request`, `devfreq_qos.c:qos_remove_request`, `devfreq_qos.c:qos_get_value` - Underlying min/max frequency constraint list manager.
- `devfreq_ondemand.c:devfreq_ondemand`, `devfreq_performance.c:devfreq_performance`, `devfreq_powersave.c:devfreq_powersave` - Built-in devfreq governor implementations (`devfreq_ondemand.c:devfreq_ondemand_s`).
- `devfreq_procfs.c:devfreq_procfs_initialize`, `devfreq_procfs.c:devfreq_procfs_s` - Registers the `/proc/devfreq` procfs entry.

## Invariants
- `devfreq.c:devfreq_register` requires valid `profile` and `governor` pointers (`profile != NULL && governor != NULL`), returning `-EINVAL` otherwise.
- Device state mutations and frequency target transitions (`devfreq_update`) must hold `devfreq->lock` (`nxmutex_lock`), while global device list traversals hold `g_devfreq_lock` (`spin_lock_irqsave`).
- `devfreq_procfs.c:devfreq_procfs_initialize` asserts `ret == 0` when registering the procfs entry.

## Side Effects
- Invokes hardware `profile->target` callbacks to adjust device operating frequency and notifies registered listeners via `atomic_notifier_call_chain` (`devfreq.c:devfreq_get_frequency`).
- Schedules periodic polling work on the low-priority work queue (`work_queue` in `devfreq_ondemand.c:devfreq_ondemand`).
- Allocates `devfreq_s`, QoS request nodes, and procfs structures via `kmm_zalloc` (`devfreq.c:devfreq_register`, `devfreq_qos.c:qos_add_request`, `devfreq_procfs.c:devfreq_procfs_initialize`).

## Verification
- Run: `make test`
