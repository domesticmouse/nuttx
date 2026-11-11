# jz4780 (`nuttx/arch/mips/src/jz4780`)

## Overview
Hardware abstraction and architecture package for `jz4780` (JZ4780 Configuration Options; JZ4780 Peripheral Support) under `nuttx/arch/mips/src/jz4780`, providing 8 header file(s) and 12 source file(s) (including `chip.h`, `jz4780_cache.h`, `jz4780_ehci.h`, `jz4780_excptmacros.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/mips/src/jz4780/hardware`, providing 1 header file(s) and 0 source file(s) (including `jz4780_pinmap.h`).

## Interface
- `[chip.h:JZ4780_DCACHE_LINESIZE]`
- `[jz4780_cache.h:m32_size_cache]`
- `[jz4780_cache.h:m32_flush_dcache]`
- `[jz4780_cache.h:m32_flush_icache]`
- `[jz4780_cache.h:m32_clean_cache]`
- `[jz4780_cache.h:m32_clean_icache]`
- `[jz4780_cache.h:m32_sync_icache]`
- `[jz4780_cache.h:m32_dcache_clean_invalidate]`
- `[jz4780_cache.h:m32_dcache_invalidate]`
- `[jz4780_cache.h:m32_dcache_clean]`
- `[jz4780_ehci.h:JZ_UHPEHCI_VSECTION]`
- `[jz4780_ehci.h:JZ_EHCI_NRHPORT]`
- `[jz4780_ehci.h:HCCR]`
- `[jz4780_ehci.h:HCOR]`
- `[jz4780_gpio.h:jz4780_configgpio]`
- `[jz4780_gpio.h:jz4780_gpiowrite]`
- `[jz4780_gpio.h:jz4780_gpioread]`
- `[jz4780_gpio.h:jz4780_gpioirqinitialize]`
- `[jz4780_gpio.h:jz4780_gpioattach]`
- `[jz4780_gpio.h:jz4780_gpioirqenable]`
- `[jz4780_gpio.h:jz4780_gpioirqdisable]`
- `[jz4780_gpio.h:jz4780_dumpgpio]`
- `[jz4780_gpio.h:pinset_t]`
- `[jz4780_gpio.h:JZ4780_BASE_GPIOA]`
- `[jz4780_gpio.h:JZ4780_BASE_GPIOB]`
- `[jz4780_gpio.h:JZ4780_BASE_GPIOC]`
- `[jz4780_gpio.h:JZ4780_BASE_GPIOD]`
- `[jz4780_gpio.h:JZ4780_BASE_GPIOE]`
- `[jz4780_gpio.h:JZ4780_BASE_GPIOF]`
- `[jz4780_gpio.h:GPIO_PXPIN]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[jz4780_cache.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[jz4780_decodeirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[jz4780_ehci.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[jz4780_ehci.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[jz4780_ehci.c:#error]` Compile-time configuration constraint: Work queue support is required (CONFIG_SCHED_WORKQUEUE)
- `[jz4780_exception.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[jz4780_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[jz4780_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[jz4780_ohci.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[jz4780_ohci.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[jz4780_ohci.c:#error]` Compile-time configuration constraint: Work queue support is required (CONFIG_SCHED_WORKQUEUE)

## Side Effects
- `[jz4780_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[jz4780_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[jz4780_decodeirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[jz4780_decodeirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[jz4780_ehci.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[jz4780_ehci.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[jz4780_ehci.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[jz4780_ehci.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[jz4780_ehci.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[jz4780_ehci.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[jz4780_ehci.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[jz4780_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
