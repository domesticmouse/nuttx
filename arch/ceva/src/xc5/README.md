# xc5 (`nuttx/arch/ceva/src/xc5`)

## Overview
Hardware abstraction and architecture package for `xc5` (XC5 Configuration Options) under `nuttx/arch/ceva/src/xc5`, providing 2 header file(s) and 7 source file(s) (including `cpm.h`, `psu.h`, `xc5_hardfault.c`, `xc5_icache.c`).

## Interface
- `[cpm.h:getcpm]`
- `[cpm.h:putcpm]`
- `[cpm.h:modifycpm]`
- `[psu.h:up_psu_lp]`
- `[psu.h:XC5_DOZE]`
- `[psu.h:XC5_IDLE]`
- `[xc5_hardfault.c:ceva_hardfault]`
- `[xc5_icache.c:up_enable_icache]`
- `[xc5_icache.c:up_disable_icache]`
- `[xc5_icache.c:up_invalidate_icache]`
- `[xc5_icache.c:up_invalidate_icache_all]`
- `[xc5_icache.c:up_coherent_dcache]`
- `[xc5_initialstate.c:up_initial_state]`
- `[xc5_intc.c:up_disable_irq]`
- `[xc5_intc.c:up_enable_irq]`
- `[xc5_intc.c:up_prioritize_irq]`
- `[xc5_intc.c:up_trigger_irq]`
- `[xc5_intc.c:up_irqinitialize]`
- `[xc5_mpu.c:mpu_control]`
- `[xc5_mpu.c:mpu_user_code]`
- `[xc5_mpu.c:mpu_priv_code]`
- `[xc5_mpu.c:mpu_user_data]`
- `[xc5_mpu.c:mpu_priv_data]`
- `[xc5_mpu.c:mpu_peripheral]`
- `[xc5_mpu.c:mpu_stronglyordered]`
- `[xc5_psu.c:up_psu_lp]`
- `[xc5_relocate.c:up_relocate]`
- `[Kconfig:CONFIG_XC5_PSU_ENABLE]`

## Invariants
- `[xc5_icache.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[xc5_intc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[xc5_intc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[xc5_intc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[xc5_intc.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xc5_psu.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
