# common (`nuttx/arch/renesas/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/renesas/src/common`, providing 1 header file(s) and 13 source file(s) (including `renesas_internal.h`, `renesas_allocateheap.c`, `renesas_createstack.c`, `renesas_doirq.c`).

## Interface
- `[renesas_internal.h:renesas_copystate]`
- `[renesas_internal.h:renesas_dataabort]`
- `[renesas_internal.h:renesas_decodeirq]`
- `[renesas_internal.h:renesas_doirq]`
- `[renesas_internal.h:renesas_prefetchabort]`
- `[renesas_internal.h:renesas_sigdeliver]`
- `[renesas_internal.h:renesas_syscall]`
- `[renesas_internal.h:renesas_lowputc]`
- `[renesas_internal.h:renesas_lowputs]`
- `[renesas_internal.h:renesas_vectorundefinsn]`
- `[renesas_internal.h:renesas_vectorswi]`
- `[renesas_internal.h:renesas_vectorprefetch]`
- `[renesas_internal.h:renesas_vectordata]`
- `[renesas_internal.h:renesas_vectoraddrexcptn]`
- `[renesas_internal.h:renesas_vectorirq]`
- `[renesas_internal.h:renesas_vectorfiq]`
- `[renesas_internal.h:renesas_earlyconsoleinit]`
- `[renesas_internal.h:renesas_consoleinit]`
- `[renesas_internal.h:renesas_serialinit]`
- `[renesas_internal.h:renesas_lcdinit]`
- `[renesas_internal.h:renesas_lcdputc]`
- `[renesas_internal.h:renesas_netinitialize]`
- `[renesas_internal.h:renesas_usbinitialize]`
- `[renesas_internal.h:renesas_usbuninitialize]`
- `[renesas_internal.h:___ARCH_RENESAS_SRC_COMMON_UP_INTERNAL_H]`
- `[renesas_internal.h:USE_SERIALDRIVER]`
- `[renesas_internal.h:USE_EARLYSERIALINIT]`
- `[renesas_internal.h:CONFIG_ARCH_INTERRUPTSTACK]`
- `[renesas_internal.h:renesas_savestate]`
- `[renesas_internal.h:getreg8]`

## Invariants
- `[renesas_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[renesas_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[renesas_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[renesas_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[renesas_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[renesas_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[renesas_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
