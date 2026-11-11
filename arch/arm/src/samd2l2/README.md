# samd2l2 (`nuttx/arch/arm/src/samd2l2`)

## Overview
Hardware abstraction and architecture package for `samd2l2` (Atmel SAMD/L Configuration Options; SAMD/L Peripheral Support) under `nuttx/arch/arm/src/samd2l2`, providing 28 header file(s) and 22 source file(s) (including `chip.h`, `sam_ac.h`, `sam_adc.h`, `sam_clockconfig.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/samd2l2/hardware`, providing 52 header file(s) and 0 source file(s) (including `samd20_memorymap.h`, `samd20_pinmap.h`, `samd21_memorymap.h`, `samd21_pinmap.h`).

## Interface
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[sam_ac.h:sam_ac_initialize]`
- `[sam_ac.h:sam_ac_config]`
- `[sam_ac.h:sam_ac_enable]`
- `[sam_adc.h:sam_adcinitialize]`
- `[sam_clockconfig.h:sam_clockconfig]`
- `[sam_config.h:SAMD2L2_HAVE_USART0]`
- `[sam_config.h:SAMD2L2_HAVE_USART1]`
- `[sam_config.h:SAMD2L2_HAVE_USART2]`
- `[sam_config.h:SAMD2L2_HAVE_USART3]`
- `[sam_config.h:SAMD2L2_HAVE_USART4]`
- `[sam_config.h:SAMD2L2_HAVE_USART5]`
- `[sam_config.h:SAMD2L2_HAVE_USART]`
- `[sam_config.h:HAVE_SERIAL_CONSOLE]`
- `[sam_config.h:SAM_CONSOLE_RS485_DIR]`
- `[sam_config.h:SAM_CONSOLE_RS485_DIR_POLARITY]`
- `[sam_dmac.h:sam_dmachannel]`
- `[sam_dmac.h:sam_dmaconfig]`
- `[sam_dmac.h:sam_dmafree]`
- `[sam_dmac.h:sam_dmatxsetup]`
- `[sam_dmac.h:sam_dmarxsetup]`
- `[sam_dmac.h:sam_dmastart]`
- `[sam_dmac.h:sam_dmastop]`
- `[sam_dmac.h:sam_dmasample]`
- `[sam_dmac.h:sam_dmadump]`
- `[sam_dmac.h:sam_dmaregs_s]`
- `[sam_dmac.h:DMA_HANDLE]`
- `[sam_dmac.h:DMACH_FLAG_BEATSIZE_SHIFT]`
- `[sam_dmac.h:DMACH_FLAG_BEATSIZE_MASK]`
- `[sam_dmac.h:DMACH_FLAG_BEATSIZE_BYTE]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_ac.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_adc.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_dac.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_dmac.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_eic.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_evsys.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_fuses.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_gclk.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_pinmap.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_port.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture
- `[sam_sercom.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture

## Side Effects
- `[samd_periphclks.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[samd_periphclks.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[saml_periphclks.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[saml_periphclks.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[sam_ac.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam_ac.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sam_ac.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[sam_ac.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[sam_ac.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[sam_ac.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[sam_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam_adc.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
