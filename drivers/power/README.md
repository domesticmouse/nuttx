# Power Subsystem (`drivers/power`)

## Overview
Groups the NuttX power management, voltage/current supply regulation, battery management, and power relay driver subsystems.

## Subdirectories & Boundaries
- `pm`: [./pm/README.md](./pm/README.md) - System-wide Power Management (PM) domains, wakelocks, runtime PM, idle-loop integration, and state governors.
- `supply`: [./supply/README.md](./supply/README.md) - Voltage/current regulator framework, SMPS and power-LED upper halves, and PMIC/buck-boost hardware drivers.
- `battery`: [./battery/README.md](./battery/README.md) - Battery charger, fuel gauge, and battery monitor upper-half frameworks and IC drivers.
- `relay`: [./relay/README.md](./relay/README.md) - Power relay upper-half character driver and GPIO relay implementation.
