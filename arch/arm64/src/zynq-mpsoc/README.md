# zynq-mpsoc (`nuttx/arch/arm64/src/zynq-mpsoc`)

## Overview
Hardware abstraction and architecture package for `zynq-mpsoc` (XILINX ZYNQ_MPSOC Peripheral Selection; Ethernet Configuration) under `nuttx/arch/arm64/src/zynq-mpsoc`, providing 5 header file(s) and 5 source file(s) (including `chip.h`, `zynq_boot.h`, `zynq_enet.h`, `zynq_mio.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/zynq-mpsoc/hardware`, providing 3 header file(s) and 0 source file(s) (including `zynq_gmac.h`, `zynq_memorymap.h`, `zynq_pll.h`).

## Interface
- `[zynq_boot.h:zynq_board_initialize]`
- `[zynq_enet.h:zynq_gmac_initialize]`
- `[zynq_enet.h:zynq_phy_boardinitialize]`
- `[zynq_enet.h:zynq_phyread]`
- `[zynq_enet.h:zynq_phywrite]`
- `[zynq_enet.h:phy_interface_s]`
- `[zynq_enet.h:phy_s]`
- `[zynq_enet.h:zynq_gmac_s]`
- `[zynq_enet.h:EMAC_INTF]`
- `[zynq_mio.h:zynq_mio_initialize]`
- `[zynq_mio.h:zynq_mio_read]`
- `[zynq_mio.h:zynq_mio_readpin]`
- `[zynq_mio.h:zynq_mio_write]`
- `[zynq_mio.h:zynq_mio_writepin]`
- `[zynq_mio.h:zynq_mio_setdir]`
- `[zynq_mio.h:zynq_mio_setdirpin]`
- `[zynq_mio.h:zynq_mio_getdir]`
- `[zynq_mio.h:zynq_mio_getdirpin]`
- `[zynq_mio.h:zynq_mio_setouten]`
- `[zynq_mio.h:zynq_mio_setoutenpin]`
- `[zynq_mio.h:zynq_mio_getouten]`
- `[zynq_mio.h:zynq_mio_getoutenpin]`
- `[zynq_mio.h:ZYNQ_MIO_MAX_BANK]`
- `[zynq_mio.h:ZYNQ_MIO_PIN_MAX]`
- `[zynq_boot.c:arm64_el_init]`
- `[zynq_boot.c:up_cpu_index]`
- `[zynq_boot.c:arm64_get_mpid]`
- `[zynq_boot.c:arm64_get_cpuid]`
- `[zynq_boot.c:arm64_chip_boot]`
- `[zynq_enet.c:zynq_phyread]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[zynq_enet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[zynq_enet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[zynq_enet.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[zynq_mio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[zynq_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[zynq_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[zynq_enet.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[zynq_enet.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[zynq_enet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[zynq_enet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[zynq_enet.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[zynq_enet.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[zynq_enet.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[zynq_mio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[zynq_mio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[zynq_pll.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[zynq_pll.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[zynq_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
