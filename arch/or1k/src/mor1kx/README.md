# mor1kx (`nuttx/arch/or1k/src/mor1kx`)

## Overview
Hardware abstraction and architecture package for `mor1kx` (OpenRISC Configuration Options; OpenRISC Options) under `nuttx/arch/or1k/src/mor1kx`, providing 1 header file(s) and 3 source file(s) (including `mor1kx_start.h`, `mor1kx_serial.c`, `mor1kx_start.c`, `or1k_irq.c`).

## Interface
- `[mor1kx_start.h:or1k_board_initialize]`
- `[mor1kx_serial.c:or1k_earlyserialinit]`
- `[mor1kx_serial.c:or1k_serialinit]`
- `[mor1kx_serial.c:up_putc]`
- `[mor1kx_start.c:g_idle_topstack]`
- `[mor1kx_start.c:__start]`
- `[mor1kx_start.c:IDLE_STACK]`
- `[or1k_irq.c:up_irqinitialize]`
- `[or1k_irq.c:up_disable_irq]`
- `[or1k_irq.c:up_enable_irq]`
- `[or1k_irq.c:or1k_ack_irq]`
- `[or1k_irq.c:or1k_dump_pic]`
- `[Kconfig:CONFIG_OR1K_TOOLCHAIN_GNU_ELF]`
- `[Kconfig:CONFIG_OR1K_CPU_FREQUENCY]`
- `[Kconfig:CONFIG_OR1K_ICACHE]`
- `[Kconfig:CONFIG_OR1K_DCACHE]`
- `[Kconfig:CONFIG_OR1K_MMU]`
- `[Make.defs:CHIP_CSRCS]`
- `[Make.defs:CMN_CSRCS]`

## Invariants
- `[mor1kx_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[or1k_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[or1k_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[or1k_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[or1k_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
