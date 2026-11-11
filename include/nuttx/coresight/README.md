# CoreSight Debug & Trace Subsystem Headers (`include/nuttx/coresight`)

## Overview
Defines the ARM CoreSight hardware trace framework for NuttX, modelling topology components as sources (ETM, ETMv4, STM), links (Funnel, Replicator, TMC-ETF), and sinks (ETB, TPIU, TMC-ETB/ETR), and managing trace path discovery, reference counting, and hardware activation.

## Interface
- `coresight.h:coresight_dev_type_e`, `coresight.h:coresight_ops_s`, `coresight.h:coresight_desc_s`, `coresight.h:coresight_connect_s`, `coresight.h:coresight_dev_s` - CoreSight device classification, source/link/sink operation tables, board topology descriptors, and runtime device nodes.
- `coresight.h:coresight_register`, `coresight.h:coresight_unregister`, `coresight.h:coresight_enable`, `coresight.h:coresight_disable` - CoreSight topology registration and end-to-end trace path activation/deactivation.
- `coresight_etb.h:coresight_etb_dev_s`, `coresight_etb.h:etb_register`, `coresight_etb.h:etb_unregister` - Embedded Trace Buffer (ETB) sink driver.
- `coresight_etm.h:etm_config_s`, `coresight_etm.h:coresight_etm_dev_s`, `coresight_etm.h:etm_register`, `coresight_etm.h:etm_unregister`, `coresight_etm.h:etm_config` - Embedded Trace Macrocell v3 (ETM) processor trace source driver.
- `coresight_etm4.h:etm4_config_s`, `coresight_etm4.h:coresight_etm4_dev_s`, `coresight_etm4.h:etm4_register`, `coresight_etm4.h:etm4_unregister`, `coresight_etm4.h:etm4_config` - Embedded Trace Macrocell v4 (ETMv4) processor trace source driver.
- `coresight_funnel.h:coresight_funnel_dev_s`, `coresight_funnel.h:set_funnel_priority`, `coresight_funnel.h:funnel_register`, `coresight_funnel.h:funnel_unregister` - Trace funnel (merger link) driver.
- `coresight_replicator.h:coresight_replicator_dev_s`, `coresight_replicator.h:replicator_register`, `coresight_replicator.h:replicator_unregister` - Trace replicator (splitter link) driver.
- `coresight_stm.h:coresight_stm_dev_s`, `coresight_stm.h:stm_set_channel_options`, `coresight_stm.h:stm_sendpacket`, `coresight_stm.h:stm_register`, `coresight_stm.h:stm_unregister` - System Trace Macrocell (STM) software stimulus trace source driver.
- `coresight_tmc.h:coresight_tmc_dev_s`, `coresight_tmc.h:tmc_register`, `coresight_tmc.h:tmc_unregister` - Trace Memory Controller (TMC ETB/ETR/ETF) driver.
- `coresight_tpiu.h:coresight_tpiu_dev_s`, `coresight_tpiu.h:tpiu_register`, `coresight_tpiu.h:tpiu_unregister` - Trace Port Interface Unit (TPIU) external sink driver.

## Invariants
- `coresight.h:coresight_desc_s.outports` is bounded by `CONFIG_CORESIGHT_MAX_OUTPORT_NUM`.
- `coresight.h:coresight_dev_s`, `coresight_funnel.h:coresight_funnel_dev_s`, and `coresight_replicator.h:coresight_replicator_dev_s` maintain per-device and per-port `refcnt` counters so shared links/sinks remain active until all active trace paths through them are disabled.

## Side Effects
- `coresight.h:coresight_register` and component-specific `*_register` functions allocate device nodes, acquire clocks (`CONFIG_CLK`), register power management callbacks (`CONFIG_PM`), and expose trace capture character devices (for ETB/TMC sinks).
- `coresight.h:coresight_enable`, `coresight_etm.h:etm_config`, `coresight_etm4.h:etm4_config`, and `coresight_stm.h:stm_sendpacket` directly program CoreSight MMIO registers and stimulus ports.

## Verification
- Run: `make test`
