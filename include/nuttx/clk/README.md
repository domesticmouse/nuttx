# Clock Tree Subsystem Headers (`include/nuttx/clk`)

## Overview
Provides the consumer and provider interfaces for the NuttX Common Clock Framework (`CONFIG_CLK`), managing hierarchical clock trees, enable/disable reference counts, frequency rate rounding/propagation, phase control, and standard hardware clock primitives (gates, dividers, multiplexers, multipliers, fixed-rate/factor clocks, and RPMSG remote clocks).

## Interface
- `clk.h:clk_s`, `clk.h:clk_rate_s`, `clk.h:clk_get`, `clk.h:clk_get_parent`, `clk.h:clk_get_parent_by_index`, `clk.h:clk_set_parent`, `clk.h:clk_enable`, `clk.h:clk_disable`, `clk.h:clk_is_enabled`, `clk.h:clk_round_rate`, `clk.h:clk_set_rate`, `clk.h:clk_set_rates`, `clk.h:clk_get_rate`, `clk.h:clk_set_phase`, `clk.h:clk_get_phase`, `clk.h:clk_disable_unused`, `clk.h:clk_get_name` - Consumer APIs for looking up, enabling, gating, reparenting, and configuring clock frequencies and phases.
- `clk_provider.h:clk_ops_s`, `clk_provider.h:clk_gate_s`, `clk_provider.h:clk_fixed_rate_s`, `clk_provider.h:clk_fixed_factor_s`, `clk_provider.h:clk_divider_s`, `clk_provider.h:clk_fractional_divider_s`, `clk_provider.h:clk_multiplier_s`, `clk_provider.h:clk_mux_s`, `clk_provider.h:clk_phase_s` - Clock provider operation vtable and hardware primitive descriptors.
- `clk_provider.h:clk_register`, `clk_provider.h:clk_register_gate`, `clk_provider.h:clk_register_fixed_rate`, `clk_provider.h:clk_register_fixed_factor`, `clk_provider.h:clk_register_divider`, `clk_provider.h:clk_register_phase`, `clk_provider.h:clk_register_fractional_divider`, `clk_provider.h:clk_register_multiplier`, `clk_provider.h:clk_register_mux`, `clk_provider.h:clk_register_rpmsg`, `clk_provider.h:clk_rpmsg_server_initialize` - Clock provider registration functions.

## Invariants
- `clk_provider.h:clk_s` tracks nested activation via `enable_count`; clocks marked with `CLK_IS_CRITICAL` remain enabled and are skipped by `clk.h:clk_disable_unused`.
- Clocks flagged with `CLK_SET_RATE_GATE` or `CLK_SET_PARENT_GATE` must be disabled (`enable_count == 0`) before their rate or parent can be modified.

## Side Effects
- `clk.h:clk_enable`, `clk.h:clk_disable`, `clk.h:clk_set_rate`, `clk.h:clk_set_parent`, and `clk.h:clk_set_phase` mutate hardware clock controller registers (gates, PLLs, muxes, dividers) and recursively update parent/child clock tree state or send RPMSG requests across cores.
- `clk_provider.h:clk_register*` functions allocate `clk_s` nodes and link them into the global clock hierarchy list.

## Verification
- Run: `make test`
