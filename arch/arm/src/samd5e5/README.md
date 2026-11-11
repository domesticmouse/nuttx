# samd5e5 (`nuttx/arch/arm/src/samd5e5`)

## Overview
Hardware abstraction and architecture package for `samd5e5` (Microchip SAMD5x/E5x Configuration Options; SAMD5x/E5x Peripheral Support) under `nuttx/arch/arm/src/samd5e5`, providing 26 header file(s) and 29 source file(s) (including `chip.h`, `sam_clockconfig.h`, `sam_cmcc.h`, `sam_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/samd5e5/hardware`, providing 29 header file(s) and 0 source file(s) (including `sam_aes.h`, `sam_cmcc.h`, `sam_dmac.h`, `sam_eic.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[sam_clockconfig.h:sam_clock_configure]`
- `[sam_clockconfig.h:sam_clock_initialize]`
- `[sam_clockconfig.h:sam_xosc32_config_s]`
- `[sam_clockconfig.h:sam_xosc_config_s]`
- `[sam_clockconfig.h:sam_dfll_config_s]`
- `[sam_clockconfig.h:sam_dpll_config_s]`
- `[sam_clockconfig.h:sam_clockconfig_s]`
- `[sam_cmcc.h:sam_cmcc_enable]`
- `[sam_cmcc.h:sam_cmcc_disable]`
- `[sam_cmcc.h:sam_cmcc_invalidate]`
- `[sam_cmcc.h:sam_cmcc_invalidateall]`
- `[sam_config.h:SAMD5E5_HAVE_USART0]`
- `[sam_config.h:SAMD5E5_HAVE_USART1]`
- `[sam_config.h:SAMD5E5_HAVE_USART2]`
- `[sam_config.h:SAMD5E5_HAVE_USART3]`
- `[sam_config.h:SAMD5E5_HAVE_USART4]`
- `[sam_config.h:SAMD5E5_HAVE_USART5]`
- `[sam_config.h:SAMD5E5_HAVE_USART6]`
- `[sam_config.h:SAMD5E5_HAVE_USART7]`
- `[sam_config.h:SAMD5E5_HAVE_USART]`
- `[sam_config.h:HAVE_SERIAL_CONSOLE]`
- `[sam_dmac.h:sam_dmachannel]`
- `[sam_dmac.h:sam_dmaconfig]`
- `[sam_dmac.h:sam_dmafree]`
- `[sam_dmac.h:sam_dmatxsetup]`
- `[sam_dmac.h:sam_dmarxsetup]`
- `[sam_dmac.h:sam_dmastart]`
- `[sam_dmac.h:sam_dmastop]`
- `[sam_dmac.h:sam_dmasample]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[sam_ethernet.h:#error]` Compile-time guard: ETH0 PHY unrecognized
- `[sam_clockconfig.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam_cmcc.c:#error]` Compile-time configuration constraint: Unknown cache line size
- `[sam_dmac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam_dmac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam_freerun.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam_freerun.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam_gclk.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam_gmac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam_gmac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam_gmac.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[sam_i2c_master.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[sam_gclk.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sam_periphclks.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[sam_periphclks.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[sam_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sam_clockconfig.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[sam_clockconfig.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[sam_cmcc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam_cmcc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sam_dmac.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam_dmac.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sam_dmac.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
