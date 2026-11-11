# NuttX Reset Controller Subsystem (`include/nuttx/reset`)

## Overview
Defines the consumer API (`reset.h`) and provider driver registration interface (`reset-controller.h`) for hardware reset lines and reset controllers, including RPMsg remote reset control support.

## Interface
- `reset.h:reset_control`, `reset.h:reset_control_get`, `reset.h:reset_control_get_exclusive`, `reset.h:reset_control_get_shared`, `reset.h:reset_control_array_get`, `reset.h:reset_control_put` - Consumer handle acquisition and release functions for exclusive, shared, or arrayed hardware reset lines.
- `reset.h:reset_control_reset`, `reset.h:reset_control_assert`, `reset.h:reset_control_deassert`, `reset.h:reset_control_status`, `reset.h:reset_control_acquire`, `reset.h:reset_control_release` - Reset pulse execution, manual assertion/deassertion, status querying, and exclusive ownership transfer.
- `reset-controller.h:reset_controller_dev`, `reset-controller.h:reset_control_ops`, `reset-controller.h:reset_lineinfo_s`, `reset-controller.h:reset_controller_register`, `reset-controller.h:reset_controller_unregister` - Reset controller provider descriptor, hardware callback table, and registration functions.
- `reset-controller.h:reset_rpmsg_get`, `reset-controller.h:reset_rpmsg_server_init` - Cross-core RPMsg reset controller client and server initialization.

## Invariants
- Shared reset lines obtained via `reset.h:reset_control_get_shared` reference-count `assert`/`deassert` calls so a shared peripheral remains out of reset as long as at least one consumer holds it deasserted.
- Exclusive reset lines obtained via `reset.h:reset_control_get_exclusive_released` require an explicit `reset.h:reset_control_acquire` call before `reset.h:reset_control_assert` or `reset.h:reset_control_deassert` may be invoked.

## Side Effects
- Calling `reset.h:reset_control_reset`, `reset.h:reset_control_assert`, or `reset.h:reset_control_deassert` mutates SoC reset controller registers (or sends RPMsg requests via `reset-controller.h:reset_rpmsg_get`), resetting hardware blocks.

## Verification
- Run: `make test`
