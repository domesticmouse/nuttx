# hw (`nuttx/arch/misoc/src/common/hw`)

## Overview
Hardware abstraction and architecture package for `hw` under `nuttx/arch/misoc/src/common/hw`, providing 3 header file(s) and 0 source file(s) (including `common.h`, `ethmac_mem.h`, `flags.h`).

## Interface
- `[common.h:CSR_ACCESSORS_DEFINED]`
- `[common.h:MMPTR]`
- `[ethmac_mem.h:ETHMAC_RX0_BASE]`
- `[ethmac_mem.h:ETHMAC_RX1_BASE]`
- `[ethmac_mem.h:ETHMAC_TX0_BASE]`
- `[ethmac_mem.h:ETHMAC_TX1_BASE]`
- `[flags.h:UART_EV_TX]`
- `[flags.h:UART_EV_RX]`
- `[flags.h:DFII_CONTROL_SEL]`
- `[flags.h:DFII_CONTROL_CKE]`
- `[flags.h:DFII_CONTROL_ODT]`
- `[flags.h:DFII_CONTROL_RESET_N]`
- `[flags.h:DFII_COMMAND_CS]`
- `[flags.h:DFII_COMMAND_WE]`
- `[flags.h:DFII_COMMAND_CAS]`
- `[flags.h:DFII_COMMAND_RAS]`
- `[flags.h:DFII_COMMAND_WRDATA]`
- `[flags.h:DFII_COMMAND_RDDATA]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
