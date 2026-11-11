# eic7700x (`nuttx/arch/risc-v/src/eic7700x`)

## Overview
Hardware abstraction and architecture package for `eic7700x` (EIC7700X Configuration Options) under `nuttx/arch/risc-v/src/eic7700x`, providing 7 header file(s) and 15 source file(s) (including `chip.h`, `eic7700x_clk.h`, `eic7700x_cpuclk.h`, `eic7700x_memorymap.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/eic7700x/hardware`, providing 6 header file(s) and 0 source file(s) (including `eic7700x_clk.h`, `eic7700x_l3cache.h`, `eic7700x_memorymap.h`, `eic7700x_pinctrl.h`).

## Interface
- `[eic7700x_clk.h:eic7700x_clk_initialize]`
- `[eic7700x_clk.h:eic7700x_clk_count]`
- `[eic7700x_clk.h:eic7700x_clk_pll_s]`
- `[eic7700x_clk.h:eic7700x_clk_div_s]`
- `[eic7700x_clk.h:eic7700x_clk_mux_s]`
- `[eic7700x_cpuclk.h:eic7700x_cpuclk_measure]`
- `[eic7700x_cpuclk.h:eic7700x_cpuclk_rates]`
- `[eic7700x_cpuclk.h:eic7700x_cpuclk_setrate]`
- `[eic7700x_cpuclk.h:eic7700x_cpuclk_initialize]`
- `[eic7700x_memorymap.h:EIC7700X_IDLESTACK_BASE]`
- `[eic7700x_mm_init.h:eic7700x_kernel_mappings]`
- `[eic7700x_mm_init.h:eic7700x_mm_init]`
- `[eic7700x_pinctrl.h:eic7700x_pinctrl_initialize]`
- `[eic7700x_pinctrl.h:eic7700x_pinctrl_count]`
- `[eic7700x_pinctrl.h:eic7700x_pad_name]`
- `[eic7700x_pinctrl.h:eic7700x_pad_funcname]`
- `[eic7700x_pinctrl.h:eic7700x_pad_lookup]`
- `[eic7700x_pinctrl.h:eic7700x_pad_config]`
- `[eic7700x_pinctrl.h:eic7700x_padshape_e]`
- `[eic7700x_pinctrl.h:eic7700x_pad_s]`
- `[eic7700x_pinctrl.h:HAVE_PINCTRL_TEXT]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_NDEFAULTS]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_NGPIOS]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_NOPAD]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_NOGPIO]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_LOCKED]`
- `[eic7700x_reset.h:eic7700x_reset_initialize]`
- `[eic7700x_reset.h:eic7700x_reset_count]`
- `[eic7700x_reset.h:eic7700x_reset_getline]`
- `[eic7700x_reset.h:eic7700x_reset_reg_s]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[chip.h:#error]` Compile-time guard: CONFIG_SMP_NCPUS must be 4: the firmware may boot NuttX on any Hart
- `[eic7700x_cache.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[eic7700x_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[eic7700x_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[eic7700x_mm_init.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[eic7700x_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[eic7700x_pgalloc.c:#error]` Compile-time configuration constraint: Page pool has more pages than the granule allocator can count
- `[eic7700x_pinctrl.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[eic7700x_pinctrl.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[eic7700x_reset.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[eic7700x_reset.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[eic7700x_start.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation

## Side Effects
- `[eic7700x_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[eic7700x_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[eic7700x_clk_ops.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[eic7700x_clk_ops.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[eic7700x_cpuclk.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[eic7700x_cpuclk.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[eic7700x_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[eic7700x_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[eic7700x_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[eic7700x_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[eic7700x_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[eic7700x_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
