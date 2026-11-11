# Thermal Management Framework (`drivers/thermal`)

## Overview
Implements the NuttX thermal management subsystem, including thermal zone devices, cooling devices, thermal governors (`thermal_core.c`), step-wise temperature trip-point governor (`thermal_step_wise.c`), DVFS/devfreq cooling integration (`thermal_devfreq_cooling.c`), procfs status reporting (`thermal_procfs.c`), and a dummy thermal zone/cooling driver for testing (`thermal_dummy.c`).

## Interface
- `[thermal_core.c:thermal_zone_device_register]`, `[thermal_core.c:thermal_zone_device_unregister]`, `[thermal_core.c:thermal_zone_device_update]`, `[thermal_core.c:thermal_zone_enable]` - Registers, unregisters, updates, and enables/disables thermal zone monitoring devices.
- `[thermal_core.c:thermal_zone_get_temp]`, `[thermal_core.c:thermal_zone_get_trend]`, `[thermal_core.c:thermal_zone_get_trip_temp]`, `[thermal_core.c:thermal_zone_get_trip_type]`, `[thermal_core.c:thermal_zone_get_trip_hyst]` - Queries temperature, thermal trend, and trip point parameters for a thermal zone.
- `[thermal_core.c:thermal_cooling_device_register]`, `[thermal_core.c:thermal_cooling_device_unregister]`, `[thermal_core.h:thermal_cooling_device_update]` - Registers, unregisters, and updates cooling devices and their state limits.
- `[thermal_core.c:thermal_register_governor]`, `[thermal_core.c:thermal_unregister_governor]`, `[thermal_step_wise.c:thermal_register_step_wise_governor]` - Registers and unregisters thermal control governors, including the built-in `step_wise` governor.
- `[thermal_devfreq_cooling.c:thermal_devfreq_cooling_register]`, `[thermal_devfreq_cooling.c:thermal_devfreq_cooling_unregister]` - Bridges `devfreq` frequency-scaling devices into thermal cooling devices.
- `[thermal_procfs.c:thermal_zone_procfs_register]`, `[thermal_procfs.c:thermal_zone_procfs_unregister]` - Exposes thermal zone temperatures and cooling states under `/proc/thermal`.
- `[thermal_dummy.c:thermal_dummy_init]` - Initializes a simulated thermal zone, cooling device, and devfreq table for testing.

## Invariants
- `[thermal_core.c:thermal_zone_device_register]` requires valid zone name and operations (`zdev->ops->get_temp`), and binds instances only when trip indices and cooling states fall within `[lower, upper]` bounds.
- `[thermal_procfs.c:thermal_zone_procfs_register]` and procfs open/read callbacks assert `DEBUGASSERT(dir)` and acquire the global thermal lock.
- `[thermal_dummy.c:thermal_dummy_init]` asserts `DEBUGASSERT(index < driver->table_len)` when indexing simulated devfreq frequencies.

## Side Effects
- `[thermal_core.c:thermal_zone_device_update]` acquires the global mutex `g_thermal_lock` (`nxmutex_lock`), polls hardware temperature sensors, invokes governor `throttle` callbacks, mutates cooling device states (`ops->set_cur_state`), schedules periodic monitoring on `LPWORK` (`work_queue`), and triggers emergency shutdown (`boardctl(BOARDIOC_POWEROFF, 0)`) when critical trip temperatures are exceeded.
- `[thermal_procfs.c:thermal_zone_procfs_register]` registers `/proc/thermal` entries in the procfs filesystem.

## Verification
- Run: `make test`
