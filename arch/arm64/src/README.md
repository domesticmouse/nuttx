# src (`nuttx/arch/arm64/src`)

## Overview
Architectural grouping for `nuttx/arch/arm64/src`, coordinating 13 component subdirectories (`a527`, `a64`, `am62x`, `bcm2711`, `common`, `fvp-v8r`, `goldfish`, `imx8`, and 5 more).

## Subdirectories & Boundaries
- `a527`: [./a527/README.md](./a527/README.md) - Hardware abstraction and architecture package for `a527` under `nuttx/arch/arm64/src/a527`, providing 2 header file(s) and 4 source file(s) (including `a527_boot.h`, `chip.h`, `a527_boot.c`, `a527_initialize.c`).
- `a64`: [./a64/README.md](./a64/README.md) - Hardware abstraction and architecture package for `a64` (Allwinner A64 Peripheral Selection) under `nuttx/arch/arm64/src/a64`, providing 12 header file(s) and 10 source file(s) (including `a64_boot.h`, `a64_de.h`, `a64_mipi_dphy.h`, `a64_mipi_dsi.h`).
- `am62x`: [./am62x/README.md](./am62x/README.md) - Hardware abstraction and architecture package for `am62x` (AM62x peripheral support) under `nuttx/arch/arm64/src/am62x`, providing 6 header file(s) and 5 source file(s) (including `am62x_boot.h`, `am62x_gpio.h`, `am62x_i2c.h`, `am62x_serial.h`).
- `bcm2711`: [./bcm2711/README.md](./bcm2711/README.md) - Hardware abstraction and architecture package for `bcm2711` (BCM2711 configuration options; Broadcom BCM2711 Peripheral Selection) under `nuttx/arch/arm64/src/bcm2711`, providing 11 header file(s) and 12 source file(s) (including `bcm2711_boot.h`, `bcm2711_cpustart.h`, `bcm2711_gpio.h`, `bcm2711_i2c.h`).
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/arm64/src/common`, providing 15 header file(s) and 56 source file(s) (including `addrenv.h`, `arm64_arch.h`, `arm64_arch_timer.h`, `arm64_cpu_psci.h`).
- `fvp-v8r`: [./fvp-v8r/README.md](./fvp-v8r/README.md) - Hardware abstraction and architecture package for `fvp-v8r` (FVP ARMv8-R Virt Chip Selection) under `nuttx/arch/arm64/src/fvp-v8r`, providing 3 header file(s) and 3 source file(s) (including `chip.h`, `fvp_boot.h`, `fvp_userspace.h`, `fvp_boot.c`).
- `goldfish`: [./goldfish/README.md](./goldfish/README.md) - Hardware abstraction and architecture package for `goldfish` under `nuttx/arch/arm64/src/goldfish`, providing 3 header file(s) and 3 source file(s) (including `chip.h`, `goldfish_boot.h`, `goldfish_serial.h`, `goldfish_boot.c`).
- `imx8`: [./imx8/README.md](./imx8/README.md) - Hardware abstraction and architecture package for `imx8` (i.MX8 Chip Selection; i.MX8 Peripheral Selection) under `nuttx/arch/arm64/src/imx8`, providing 3 header file(s) and 2 source file(s) (including `chip.h`, `imx8_boot.h`, `imx8_serial.h`, `imx8_boot.c`).
- `imx9`: [./imx9/README.md](./imx9/README.md) - Hardware abstraction and architecture package for `imx9` (i.MX9 Chip Selection; DMA Allocator Configuration) under `nuttx/arch/arm64/src/imx9`, providing 27 header file(s) and 31 source file(s) (including `chip.h`, `imx9_boot.h`, `imx9_ccm.h`, `imx9_clockconfig.h`).
- `qemu`: [./qemu/README.md](./qemu/README.md) - Hardware abstraction and architecture package for `qemu` (Qemu Virt Chip Selection) under `nuttx/arch/arm64/src/qemu`, providing 3 header file(s) and 5 source file(s) (including `chip.h`, `qemu_boot.h`, `qemu_serial.h`, `qemu_boot.c`).
- `rk3399`: [./rk3399/README.md](./rk3399/README.md) - Hardware abstraction and architecture package for `rk3399` (Rockchip RK3399 Peripheral Selection) under `nuttx/arch/arm64/src/rk3399`, providing 3 header file(s) and 2 source file(s) (including `chip.h`, `rk3399_boot.h`, `rk3399_serial.h`, `rk3399_boot.c`).
- `rk3588`: [./rk3588/README.md](./rk3588/README.md) - Hardware abstraction and architecture package for `rk3588` under `nuttx/arch/arm64/src/rk3588`, providing 2 header file(s) and 2 source file(s) (including `chip.h`, `rk3588_boot.h`, `rk3588_boot.c`, `rk3588_serial.c`).
- `zynq-mpsoc`: [./zynq-mpsoc/README.md](./zynq-mpsoc/README.md) - Hardware abstraction and architecture package for `zynq-mpsoc` (XILINX ZYNQ_MPSOC Peripheral Selection; Ethernet Configuration) under `nuttx/arch/arm64/src/zynq-mpsoc`, providing 5 header file(s) and 5 source file(s) (including `chip.h`, `zynq_boot.h`, `zynq_enet.h`, `zynq_mio.h`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./a527/README.md](./a527/README.md)
- [./a64/README.md](./a64/README.md)
- [./am62x/README.md](./am62x/README.md)
- [./bcm2711/README.md](./bcm2711/README.md)
- [./common/README.md](./common/README.md)
- [./fvp-v8r/README.md](./fvp-v8r/README.md)
- [./goldfish/README.md](./goldfish/README.md)
- [./imx8/README.md](./imx8/README.md)
- [./imx9/README.md](./imx9/README.md)
- [./qemu/README.md](./qemu/README.md)
- [./rk3399/README.md](./rk3399/README.md)
- [./rk3588/README.md](./rk3588/README.md)
- [./zynq-mpsoc/README.md](./zynq-mpsoc/README.md)

## Invariants
- `[a527_boot.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[a64_de.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_mipi_dsi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_pio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a64_pio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[a64_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[a64_de.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_de.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a64_mipi_dphy.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_mipi_dsi.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a64_mipi_dsi.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a64_pio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
