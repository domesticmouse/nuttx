# xm6 (`nuttx/arch/ceva/src/xm6`)

## Overview
Hardware abstraction and architecture package for `xm6` (XM6 Configuration Options) under `nuttx/arch/ceva/src/xm6`, providing 1 header file(s) and 6 source file(s) (including `cpm.h`, `xm6_hardfault.c`, `xm6_icache.c`, `xm6_initialstate.c`).

## Interface
- `[xm6_hardfault.c:ceva_hardfault]`
- `[xm6_icache.c:up_enable_icache]`
- `[xm6_icache.c:up_disable_icache]`
- `[xm6_icache.c:up_invalidate_icache]`
- `[xm6_icache.c:up_invalidate_icache_all]`
- `[xm6_icache.c:up_coherent_dcache]`
- `[xm6_initialstate.c:up_initial_state]`
- `[xm6_intc.c:up_disable_irq]`
- `[xm6_intc.c:up_enable_irq]`
- `[xm6_intc.c:up_prioritize_irq]`
- `[xm6_intc.c:up_trigger_irq]`
- `[xm6_intc.c:up_irqinitialize]`
- `[xm6_mpu.c:mpu_control]`
- `[xm6_mpu.c:mpu_user_code]`
- `[xm6_mpu.c:mpu_priv_code]`
- `[xm6_mpu.c:mpu_user_data]`
- `[xm6_mpu.c:mpu_priv_data]`
- `[xm6_mpu.c:mpu_peripheral]`
- `[xm6_mpu.c:mpu_stronglyordered]`
- `[xm6_psu.c:ceva_cpu_doze]`
- `[xm6_psu.c:ceva_cpu_idle]`
- `[Kconfig:CONFIG_ARCH_XM6_BUG001]`

## Invariants
- `[xm6_icache.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[xm6_intc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[xm6_intc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[xm6_intc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[xm6_intc.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xm6_psu.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
