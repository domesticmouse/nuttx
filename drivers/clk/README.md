# Clock Framework Drivers (`drivers/clk`)

## Overview
Implements the NuttX hierarchical clock tree framework (`clk_s`), providing clock registration, reference-counted enable/disable propagation, rate rounding and cascading updates, phase control, parent multiplexing, standard clock building blocks (divider, fractional divider, fixed factor, fixed rate, gate, multiplier, mux, phase), and RPMsg remote clock proxying.

## Interface
- `clk.c:clk_register`, `clk.c:clk_get`, `clk.c:clk_get_name`, `clk.c:clk_disable_unused` - Registers clock nodes into the global clock tree, looks up clocks by name, and disables unused clocks.
- `clk.c:clk_enable`, `clk.c:clk_disable`, `clk.c:clk_is_enabled` - Reference-counted clock enable/disable APIs that propagate up the parent chain.
- `clk.c:clk_get_rate`, `clk.c:clk_round_rate`, `clk.c:clk_set_rate`, `clk.c:clk_set_rates` - Queries, rounds, and configures clock frequencies across parent/child hierarchies.
- `clk.c:clk_get_parent`, `clk.c:clk_get_parent_by_index`, `clk.c:clk_set_parent`, `clk.c:clk_get_phase`, `clk.c:clk_set_phase` - Manages clock parent selection and phase delay (0-359 degrees).
- `clk_divider.c:clk_register_divider`, `clk_fractional_divider.c:clk_register_fractional_divider`, `clk_fixed_factor.c:clk_register_fixed_factor`, `clk_fixed_rate.c:clk_register_fixed_rate`, `clk_gate.c:clk_register_gate`, `clk_multiplier.c:clk_register_multiplier`, `clk_mux.c:clk_register_mux`, `clk_phase.c:clk_register_phase` - Registers standard hardware clock primitives.
- `clk_rpmsg.c:clk_register_rpmsg`, `clk_rpmsg_server_initialize` - Registers client/server RPMsg clock proxies for cross-core clock management (`clk_rpmsg.c:clk_rpmsg_s`).

## Invariants
- Clock tree topology and rate/enable counts (`enable_count`) are serialized by the global recursive mutex `g_clk_list_lock` (`clk.c:clk_enable`, `clk.c:clk_set_rate`).
- `clk.c:clk_set_phase` rejects `degrees < 0` or `degrees >= 360` with `-EINVAL`.
- Clocks flagged with `CLK_SET_RATE_GATE` or `CLK_SET_PARENT_GATE` cannot change rate or parent while `enable_count > 0` (`clk.c:clk_set_rate`, `clk.c:clk_set_parent`).

## Side Effects
- Acquires `g_clk_list_lock` via `nxrmutex_lock` and hardware register spinlocks via `spin_lock_irqsave` (`clk.c:clk_enable`).
- Modifies memory-mapped clock controller registers (`clk_read`, `clk_write`) to gate clocks, adjust dividers/multipliers, and switch mux parents.
- Allocates clock descriptors via `kmm_zalloc` (`clk.c:clk_register`) and exchanges cross-processor IPC messages via `rpmsg_register_callback` and `rpmsg_send` (`clk_rpmsg.c:clk_rpmsg_server_initialize`).

## Verification
- Run: `make test`
