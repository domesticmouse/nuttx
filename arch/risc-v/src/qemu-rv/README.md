# qemu-rv (`nuttx/arch/risc-v/src/qemu-rv`)

## Overview
Hardware abstraction and architecture package for `qemu-rv` (QEMU RISC-V Options) under `nuttx/arch/risc-v/src/qemu-rv`, providing 5 header file(s) and 9 source file(s) (including `chip.h`, `qemu_rv_memorymap.h`, `qemu_rv_mm_init.h`, `qemu_rv_rptun.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/qemu-rv/hardware`, providing 4 header file(s) and 0 source file(s) (including `qemu_rv_aplic.h`, `qemu_rv_clint.h`, `qemu_rv_memorymap.h`, `qemu_rv_plic.h`).

## Interface
- `[qemu_rv_memorymap.h:QEMU_RV_IDLESTACK_BASE]`
- `[qemu_rv_memorymap.h:QEMU_RV_RESET_DONE]`
- `[qemu_rv_memorymap.h:QEMU_RV_RESET_FAIL]`
- `[qemu_rv_memorymap.h:QEMU_RV_RESET_REBOOT]`
- `[qemu_rv_mm_init.h:qemu_rv_kernel_mappings]`
- `[qemu_rv_mm_init.h:qemu_rv_mm_init]`
- `[qemu_rv_rptun.h:qemu_rptun_init]`
- `[qemu_rv_rptun.h:qemu_rptun_ipi]`
- `[qemu_rv_userspace.h:qemu_rv_configure_mpu]`
- `[qemu_rv_userspace.h:qemu_rv_userspace]`
- `[qemu_rv_allocateheap.c:up_allocate_kheap]`
- `[qemu_rv_allocateheap.c:riscv_addregion]`
- `[qemu_rv_irq.c:up_irqinitialize]`
- `[qemu_rv_irq.c:up_disable_irq]`
- `[qemu_rv_irq.c:up_enable_irq]`
- `[qemu_rv_irq.c:up_irq_enable]`
- `[qemu_rv_irq_dispatch.c:riscv_dispatch_irq]`
- `[qemu_rv_mm_init.c:qemu_rv_kernel_mappings]`
- `[qemu_rv_mm_init.c:qemu_rv_mm_init]`
- `[qemu_rv_pgalloc.c:up_allocate_pgheap]`
- `[qemu_rv_rptun.c:rp_init_ipi]`
- `[qemu_rv_rptun.c:qemu_rptun_ipi]`
- `[qemu_rv_rptun.c:qemu_rptun_init]`
- `[qemu_rv_start.c:qemu_rv_start]`
- `[qemu_rv_start.c:riscv_earlyserialinit]`
- `[qemu_rv_start.c:riscv_serialinit]`
- `[qemu_rv_start.c:sbi_late_initialize]`
- `[qemu_rv_timerisr.c:up_timer_initialize]`
- `[qemu_rv_userspace.c:qemu_rv_configure_mpu]`
- `[qemu_rv_userspace.c:qemu_rv_userspace]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[qemu_rv_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[qemu_rv_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[qemu_rv_mm_init.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[qemu_rv_mm_init.c:#error]` Compile-time configuration constraint: No valid MMU defined.
- `[qemu_rv_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[qemu_rv_rptun.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[qemu_rv_start.c:#error]` Compile-time configuration constraint: Target requires kernel in S-mode, enable CONFIG_ARCH_USE_S_MODE
- `[qemu_rv_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[qemu_rv_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[qemu_rv_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[qemu_rv_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[qemu_rv_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[qemu_rv_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[qemu_rv_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[qemu_rv_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[qemu_rv_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[qemu_rv_rptun.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
