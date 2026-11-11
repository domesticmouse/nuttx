# NuttX Power Management & Battery Subsystem (`include/nuttx/power`)

## Overview
Provides the system-wide Power Management (`PM`) framework, runtime PM (`pm_runtime`), voltage/current regulator framework (`regulator` and `consumer`), switched-mode power supplies (`SMPS`), power LEDs, relays, and battery charger/gauge/monitor driver interfaces along with specific PMIC and battery IC headers.

## Interface
- `pm.h:pm_state_e`, `pm.h:pm_callback_s`, `pm.h:pm_governor_s`, `pm.h:pm_wakelock_s`, `pm.h:pm_initialize`, `pm.h:pm_domain_register`, `pm.h:pm_activity`, `pm.h:pm_stay`, `pm.h:pm_relax`, `pm.h:pm_staytimeout`, `pm.h:pm_wakelock_init`, `pm.h:pm_wakelock_stay`, `pm.h:pm_wakelock_relax`, `pm.h:pm_checkstate`, `pm.h:pm_changestate` - System power state machine (`PM_NORMAL`, `PM_IDLE`, `PM_STANDBY`, `PM_SLEEP`), driver prepare/notify callbacks, governors, and wakelocks.
- `pm_runtime.h:pm_runtime_s`, `pm_runtime.h:pm_runtime_ops_s`, `pm_runtime.h:pm_runtime_init`, `pm_runtime.h:pm_runtime_get`, `pm_runtime.h:pm_runtime_put`, `pm_runtime.h:pm_runtime_put_autosuspend` - Reference-counted per-device runtime suspend and resume API.
- `regulator.h:regulator_dev_s`, `regulator.h:regulator_ops_s`, `regulator.h:regulator_desc_s`, `regulator.h:regulator_register`, `regulator.h:regulator_unregister`, `consumer.h:regulator_get`, `consumer.h:regulator_put`, `consumer.h:regulator_enable`, `consumer.h:regulator_disable`, `consumer.h:regulator_set_voltage`, `consumer.h:regulator_get_voltage` - Regulator provider and consumer APIs.
- `battery_charger.h:battery_charger_dev_s`, `battery_charger.h:battery_charger_operations_s`, `battery_charger.h:battery_charger_register`, `battery_gauge.h:battery_gauge_dev_s`, `battery_gauge.h:battery_gauge_operations_s`, `battery_gauge.h:battery_gauge_register`, `battery_monitor.h:battery_monitor_dev_s`, `battery_monitor.h:battery_monitor_operations_s`, `battery_monitor.h:battery_monitor_register`, `battery_ioctl.h:BATIOC_STATE`, `battery_ioctl.h:BATIOC_VOLTAGE`, `battery_ioctl.h:BATIOC_CAPACITY` - Upper/lower-half battery charger, fuel gauge, and multi-cell monitor interfaces and `BATIOC_*` ioctls.
- `smps.h:smps_dev_s`, `smps.h:smps_ops_s`, `smps.h:smps_register`, `powerled.h:powerled_dev_s`, `powerled.h:powerled_ops_s`, `powerled.h:powerled_register`, `relay.h:relay_dev_s`, `relay.h:relay_ops_s`, `relay.h:relay_register`, `power_ioctl.h:PWRIOC_START`, `power_ioctl.h:PWRIOC_STOP` - SMPS, high-power LED, and relay control drivers and `PWRIOC_*` ioctls.
- `act8945a.h:act8945a_initialize`, `axp202.h:axp202_initialize`, `bq2429x.h:BQ2429X_REG00`, `bq27426.h:BQ27426_I2C_ADDRESS`, `bq769x0.h:BQ769X0_MAX_CELLS`, `gd30bc2416.h:gd30bc2416_initialize`, `lm51772.h:lm51772_register`, `ltc4013.h:ltc4013_register`, `mcp73871.h:mcp73871_initialize`, `npm1100.h:npm1100_initialize` - Hardware-specific PMIC, charger, and BMS chip configurations.

## Invariants
- Power state transitions in `pm.h:pm_state_e` proceed strictly from higher to lower power consumption (`PM_NORMAL -> PM_IDLE -> PM_STANDBY -> PM_SLEEP`) and return directly to `PM_NORMAL`.
- Drivers implementing `pm.h:pm_callback_s` (`prepare`) may veto a transition to a lower power state by returning a non-zero value, but must never return non-zero when reverting back toward a higher power state (`PM_NORMAL`).
- `pm.h:pm_initialize` must be invoked during early boot prior to registering any device driver callbacks via `pm.h:pm_domain_register`.

## Side Effects
- Calling `pm.h:pm_changestate`, `consumer.h:regulator_enable`, `consumer.h:regulator_set_voltage`, or `pm_runtime.h:pm_runtime_put` invokes driver callbacks that gate peripheral clocks, switch voltage rails, or place the CPU into WFI/deep-sleep states.
- `battery_charger.h:battery_charger_changed`, `battery_gauge.h:battery_gauge_changed`, and `battery_monitor.h:battery_monitor_changed` signal waiting pollers and blocked readers on `/dev/bat*` character devices.

## Verification
- Run: `make test`
