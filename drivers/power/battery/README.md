# Battery Charger, Gauge, and Monitor Drivers (`drivers/power/battery`)

## Overview
Provides the upper-half character driver frameworks for battery chargers (`battery_charger`), fuel gauges (`battery_gauge`), and battery monitors/BMS (`battery_monitor`), along with I2C/virtual lower-half drivers for commercial charger, fuel-gauge, and PMIC ICs.

## Interface
- `[battery_charger.c:battery_charger_register]`, `[battery_charger.c:battery_charger_changed]` - Upper-half battery charger character driver registration and state-change notification (`[battery_charger.c:struct battery_charger_priv_s]`).
- `[battery_gauge.c:battery_gauge_register]`, `[battery_gauge.c:battery_gauge_changed]` - Upper-half battery fuel-gauge character driver registration and event notification (`[battery_gauge.c:struct battery_gauge_priv_s]`).
- `[battery_monitor.c:battery_monitor_register]`, `[battery_monitor.c:battery_monitor_changed]` - Upper-half battery monitor/BMS character driver registration and event notification (`[battery_monitor.c:struct battery_monitor_priv_s]`).
- `[axp202.c:axp202_initialize]`, `[bq2425x.c:bq2425x_initialize]`, `[bq2429x.c:bq2429x_initialize]`, `[bq27426.c:bq27426_initialize]`, `[bq769x0.c:bq769x0_initialize]`, `[gd30bc2416.c:gd30bc2416_initialize]`, `[ltc4013.c:ltc4013_register]`, `[max1704x.c:max1704x_initialize]`, `[mcp73871.c:mcp73871_initialize]`, `[npm1100.c:npm1100_initialize]` - Hardware battery charger, fuel gauge, and monitor chip drivers.
- `[battery_fakegauge.c:battery_fake_gauge_register]`, `[goldfish_battery.c:goldfish_battery_register]` - Simulated fuel gauge and QEMU/Android Goldfish virtual battery drivers.

## Invariants
- Access to per-device open client lists and lower-half operations in `battery_charger.c`, `battery_gauge.c`, and `battery_monitor.c` is serialized via `dev->batlock` (`nxmutex_lock`).
- Blocking reads on battery device descriptors wait on `priv->wait` (`nxsem_wait`) until a state change mask (`priv->mask`) is signaled.

## Side Effects
- Registers VFS character devices (`register_driver`), schedules poll/notification work on `LPWORK`/`HPWORK` (`work_queue`), and performs I2C/GPIO/MMIO register transfers to configure charge voltage/current and read battery telemetry.

## Verification
- Run: `make test`
