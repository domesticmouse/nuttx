# Reset Controller Subsystem (`drivers/reset`)

## Overview
Implements the hardware Reset Controller framework in NuttX, providing consumer APIs for asserting, deasserting, pulsing, and querying reset lines (including shared/exclusive semantics, reset arrays, `/proc/reset` diagnostics, and cross-core RPMSG remote reset controllers).

## Interface
- `[core.c:reset_controller_register]`, `[core.c:reset_controller_unregister]` - Registers and unregisters a `struct reset_controller_dev` provider (`[core.c:g_reset_controller_list]`).
- `[core.c:reset_control_get]`, `[core.c:reset_control_array_get]`, `[core.c:reset_control_put]`, `[core.c:reset_control_acquire]`, `[core.c:reset_control_release]` - Acquires and releases single or grouped `struct reset_control` handles (`[core.c:struct reset_control_array]`).
- `[core.c:reset_control_reset]`, `[core.c:reset_control_assert]`, `[core.c:reset_control_deassert]`, `[core.c:reset_control_status]`, `[core.c:reset_control_device_reset]` - Triggers reset pulses, asserts/deasserts reset lines, and queries reset line status.
- `[reset_rpmsg.c:reset_rpmsg_get]`, `[reset_rpmsg.c:reset_rpmsg_server_init]` - RPMSG client and server proxy for controlling reset lines across remote processors (`[reset_rpmsg.c:struct reset_rpmsg_controller_s]`).

## Invariants
- Shared reset controls (`rstc->shared`) refcount `deassert_count` and `triggered_count` atomically so `assert` only drives hardware when the last consumer asserts it, whereas exclusive controls reject concurrent acquisition unless temporarily released via `[core.c:reset_control_release]`.
- Global controller list access is serialized via `[core.c:g_reset_list_mutex]` (`nxmutex_lock`).

## Side Effects
- Mutates hardware reset controller registers via lower-half `ops`, exchanges RPMSG messages with remote reset servers (`[reset_rpmsg.c:rpmsg_create_ept]`), and exposes `/proc/reset` when `[core.c:CONFIG_RESET_PROCFS]` is enabled.

## Verification
- Run: `make test`
