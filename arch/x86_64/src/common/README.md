# common (`nuttx/arch/x86_64/src/common`)

## Overview
Hardware abstraction and architecture package for `common` (Common Configuration Options) under `nuttx/arch/x86_64/src/common`, providing 6 header file(s) and 29 source file(s) (including `addrenv.h`, `pgalloc.h`, `x86_64_fork.h`, `x86_64_hwdebug.h`).

## Interface
- `[addrenv.h:ARCH_ADDRENV_VBASE]`
- `[addrenv.h:ARCH_ADDRENV_MAX_SIZE]`
- `[addrenv.h:ARCH_ADDRENV_VEND]`
- `[addrenv.h:MMU_KPGT_FLAGS]`
- `[addrenv.h:MMU_USER_DEFAULT]`
- `[addrenv.h:MMU_UPGT_FLAGS]`
- `[addrenv.h:MMU_UDATA_FLAGS]`
- `[addrenv.h:MMU_UTEXT_FLAGS]`
- `[x86_64_fork.h:fork_s]`
- `[x86_64_fork.h:FORK_SIZEOF]`
- `[x86_64_hwdebug.h:x86_64_hwdebug_init]`
- `[x86_64_internal.h:modifyreg8]`
- `[x86_64_internal.h:modifyreg16]`
- `[x86_64_internal.h:modifyreg32]`
- `[x86_64_internal.h:x86_64_boardinitialize]`
- `[x86_64_internal.h:x86_64_copystate]`
- `[x86_64_internal.h:x86_64_decodeirq]`
- `[x86_64_internal.h:x86_64_dmainitialize]`
- `[x86_64_internal.h:x86_64_switchcontext]`
- `[x86_64_internal.h:x86_64_sigdeliver]`
- `[x86_64_internal.h:x86_64_lowputc]`
- `[x86_64_internal.h:x86_64_lowputs]`
- `[x86_64_internal.h:x86_64_restore_auxstate]`
- `[x86_64_internal.h:x86_64_checktasks]`
- `[x86_64_internal.h:x86_64_syscall]`
- `[x86_64_internal.h:x86_64_mb2_fbinitialize]`
- `[x86_64_internal.h:fb_putc]`
- `[x86_64_internal.h:x86_64_addregion]`
- `[x86_64_internal.h:x86_64_earlyserialinit]`
- `[x86_64_internal.h:x86_64_serialinit]`

## Invariants
- `[x86_64_acpi.c:#error]` Compile-time configuration constraint: For now only ACPI from BIOS region is supported
- `[x86_64_acpi_procfs.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_addrenv.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_addrenv.c:#error]` Compile-time configuration constraint: CONFIG_RAM_VSTART != 0x100000000
- `[x86_64_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_allocateheap.c:#error]` Compile-time configuration constraint: CONFIG_IDLETHREAD_STACKSIZE must be aligned to 16
- `[x86_64_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_hwdebug.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[x86_64_mmu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[x86_64_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[x86_64_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[x86_64_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[x86_64_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[x86_64_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[x86_64_internal.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[crt0.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[x86_64_exit.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[x86_64_hwdebug.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[x86_64_hwdebug.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[x86_64_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[x86_64_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[x86_64_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[x86_64_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
