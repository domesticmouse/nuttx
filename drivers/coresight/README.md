# ARM CoreSight Trace Drivers (`drivers/coresight`)

## Overview
Implements the ARM CoreSight hardware trace topology manager and component drivers, supporting trace sources (ETMv3, ETMv4, STM), trace links (Funnel, Replicator, TMC-ETF), and trace sinks (ETB, TPIU, TMC-ETF, TMC-ETR).

## Interface
- `coresight_core.c:coresight_register`, `coresight_core.c:coresight_unregister`, `coresight_core.c:coresight_enable`, `coresight_core.c:coresight_disable` - Registers CoreSight devices (`coresight_core.c:coresight_node_s`), builds source-to-sink trace paths, and enables/disables complete trace pipelines.
- `coresight_common.c:coresight_lock`, `coresight_common.c:coresight_unlock`, `coresight_common.c:coresight_claim_device`, `coresight_common.c:coresight_disclaim_device`, `coresight_common.c:coresight_get_cpu_trace_id`, `coresight_common.c:coresight_get_system_trace_id`, `coresight_common.c:coresight_put_system_trace_id`, `coresight_common.c:coresight_timeout`, `coresight_common.c:coresight_insert_barrier_packet` - Provides CoreSight Software Lock (`CORESIGHT_LAR`), claim tag management, ATB trace ID allocation, register polling timeouts, and barrier packet insertion.
- `coresight_etm3.c:etm_register`, `coresight_etm3.c:etm_unregister`, `coresight_etm3.c:etm_config`, `coresight_etm4.c:etm4_register`, `coresight_etm4.c:etm4_unregister`, `coresight_etm4.c:etm4_config` - Registers and configures Embedded Trace Macrocell v3 and v4 instruction trace sources.
- `coresight_stm.c:stm_register`, `coresight_stm.c:stm_unregister`, `coresight_stm.c:stm_sendpacket`, `coresight_stm.c:stm_set_channel_options` - Registers System Trace Macrocell (STM) stimulus sources and transmits trace packets.
- `coresight_funnel.c:funnel_register`, `coresight_funnel.c:funnel_unregister`, `coresight_funnel.c:set_funnel_priority`, `coresight_replicator.c:replicator_register`, `coresight_replicator.c:replicator_unregister` - Registers trace funnels and ATB replicators.
- `coresight_etb.c:etb_register`, `coresight_etb.c:etb_unregister`, `coresight_tpiu.c:tpiu_register`, `coresight_tpiu.c:tpiu_unregister`, `coresight_tmc_core.c:tmc_register`, `coresight_tmc_core.c:tmc_unregister`, `coresight_tmc_etf.c:tmc_etf_register`, `coresight_tmc_etf.c:tmc_etf_unregister`, `coresight_tmc_etr.c:tmc_etr_register`, `coresight_tmc_etr.c:tmc_etr_unregister` - Registers Embedded Trace Buffer (ETB), Trace Port Interface Unit (TPIU), and Trace Memory Controller (TMC ETF/ETR) sink/link drivers.

## Invariants
- CoreSight component registers must be unlocked with `coresight_common.c:coresight_unlock` (`0xc5acce55` to `CORESIGHT_LAR`) before mutation and re-locked with `coresight_common.c:coresight_lock` afterward.
- `coresight_stm.c:stm_register` asserts `sizeof(uintptr_t) <= sizeof(unsigned long)` for stimulus port bitmap math.
- Sink character device read/open/close handlers assert `inode->i_private != NULL` (`coresight_etb.c:etb_register`, `coresight_tmc_etf.c:tmc_etf_register`, `coresight_tmc_etr.c:tmc_etr_register`).

## Side Effects
- Reads and writes memory-mapped CoreSight registers (`getreg32`, `putreg32`, ` modifyreg32`) or ARM coprocessor registers (`CONFIG_CORESIGHT_ETM_USE_COPROCESSOR` in `coresight_etm4.c:etm4_config`).
- Acquires critical sections (`enter_critical_section`), spinlocks (`spin_lock_irqsave` in `coresight_common.c:coresight_get_system_trace_id`), and mutexes (`nxmutex_lock` in `coresight_etb.c:etb_register`, `coresight_tmc_etf.c:tmc_etf_register`, `coresight_tmc_etr.c:tmc_etr_register`).
- Registers character devices under `/dev` for trace buffer readout (`register_driver` in `coresight_etb.c:etb_register`, `coresight_tmc_etf.c:tmc_etf_register`, `coresight_tmc_etr.c:tmc_etr_register`) and manages component clocks/power domains (`CONFIG_CLK`, `CONFIG_PM` in `coresight_core.c:coresight_enable`).

## Verification
- Run: `make test`
