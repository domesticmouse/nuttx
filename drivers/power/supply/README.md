# Power Supply and Voltage Regulator Drivers (`drivers/power/supply`)

## Overview
Implements the voltage/current regulator framework (core consumer/provider API, GPIO regulator, RPMSG remote regulator, and `/proc/regulator`), Switched-Mode Power Supply (`smps`) and high-power LED (`powerled`) upper-half drivers, and PMIC/buck-boost hardware drivers (ACT8945A, LM51772).

## Interface
- `[regulator.c:regulator_register]`, `[regulator.c:regulator_unregister]`, `[regulator.c:regulator_get]`, `[regulator.c:regulator_put]`, `[regulator.c:regulator_enable]`, `[regulator.c:regulator_enable_delay]`, `[regulator.c:regulator_disable]`, `[regulator.c:regulator_disable_deferred]`, `[regulator.c:regulator_is_enabled]`, `[regulator.c:regulator_set_voltage]`, `[regulator.c:regulator_get_voltage]`, `[regulator.c:regulator_set_mode]` - Core voltage regulator provider and consumer API (`[regulator.c:g_reg_list]`).
- `[regulator_gpio.c:regulator_gpio_init]` - Initializes a GPIO-controlled voltage regulator (`[regulator_gpio.c:struct regulator_gpio_priv]`).
- `[regulator_rpmsg.c:regulator_rpmsg_get]`, `[regulator_rpmsg.c:regulator_rpmsg_server_init]` - RPMSG client and server proxy for cross-core regulator control (`[regulator_rpmsg.c:struct regulator_rpmsg_client_s]`).
- `[smps.c:smps_register]`, `[powerled.c:powerled_register]` - Upper-half character drivers for Switched-Mode Power Supplies and high-power LED supplies.
- `[act8945a.c:act8945a_initialize]`, `[lm51772.c:lm51772_register]` - Hardware regulator drivers for the Qorvo ACT8945A PMIC (`[act8945a.c:struct act8945a_dev_s]`) and TI LM51772 buck-boost controller (`[lm51772.c:struct lm51772_s]`).

## Invariants
- Regulator voltage changes (`[regulator.c:_regulator_set_voltage_unlocked]`) must satisfy the intersection of `min_uv`/`max_uv` constraints across all active consumers on that rail (`[regulator.c:regulator_check_consumers]`) and respect the rail's `min_uV`/`max_uV` limits.
- Access to the global regulator list and per-device state is synchronized via `[regulator.c:g_reg_lock]` (`nxrmutex_lock`) and `[regulator.c:regulator_lock]`.

## Side Effects
- Enables/disables physical power rails, adjusts output voltages over I2C/GPIO/RPMSG, schedules deferred disable work items (`[regulator.c:work_queue]`), and registers VFS/procfs nodes (`[smps.c:register_driver]`, `[powerled.c:register_driver]`, `/proc/regulator`).

## Verification
- Run: `make test`
