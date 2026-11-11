# src (`nuttx/arch/risc-v/src`)

## Overview
Architectural grouping for `nuttx/arch/risc-v/src`, coordinating 28 component subdirectories (`ab32vg1`, `allwinner-d1`, `bl602`, `bl808`, `c906`, `common`, `eic7700x`, `erbium`, and 20 more).

## Subdirectories & Boundaries
- `ab32vg1`: [./ab32vg1/README.md](./ab32vg1/README.md) - Hardware abstraction and architecture package for `ab32vg1` (AB32VG1 Configuration Options; AB32VG1 Peripheral Support) under `nuttx/arch/risc-v/src/ab32vg1`, providing 4 header file(s) and 10 source file(s) (including `ab32vg1.h`, `ab32vg1_gpio.h`, `ab32vg1_lowputc.h`, `chip.h`).
- `allwinner-d1`: [./allwinner-d1/README.md](./allwinner-d1/README.md) - Hardware abstraction and architecture package for `allwinner-d1` under `nuttx/arch/risc-v/src/allwinner-d1`, providing 2 header file(s) and 4 source file(s) (including `allwinner_d1_memorymap.h`, `chip.h`, `allwinner_d1_irq.c`, `allwinner_d1_irq_dispatch.c`).
- `bl602`: [./bl602/README.md](./bl602/README.md) - Hardware abstraction and architecture package for `bl602` (BL602 Configuration Options; BL602 Peripheral Support) under `nuttx/arch/risc-v/src/bl602`, providing 23 header file(s) and 26 source file(s) (including `bl602_boot2.h`, `bl602_config.h`, `bl602_dma.h`, `bl602_efuse.h`).
- `bl808`: [./bl808/README.md](./bl808/README.md) - Hardware abstraction and architecture package for `bl808` (BL808 Configuration Options; BL808 Peripheral Support) under `nuttx/arch/risc-v/src/bl808`, providing 10 header file(s) and 14 source file(s) (including `bl808_gpadc.h`, `bl808_gpio.h`, `bl808_i2c.h`, `bl808_memorymap.h`).
- `c906`: [./c906/README.md](./c906/README.md) - Hardware abstraction and architecture package for `c906` (C906 Configuration Options; C906 Peripheral Support) under `nuttx/arch/risc-v/src/c906`, providing 7 header file(s) and 9 source file(s) (including `c906.h`, `c906_clockconfig.h`, `c906_config.h`, `c906_lowputc.h`).
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/risc-v/src/common`, providing 11 header file(s) and 54 source file(s) (including `addrenv.h`, `pgalloc.h`, `riscv_aia.h`, `riscv_common_memorymap.h`).
- `eic7700x`: [./eic7700x/README.md](./eic7700x/README.md) - Hardware abstraction and architecture package for `eic7700x` (EIC7700X Configuration Options) under `nuttx/arch/risc-v/src/eic7700x`, providing 7 header file(s) and 15 source file(s) (including `chip.h`, `eic7700x_clk.h`, `eic7700x_cpuclk.h`, `eic7700x_memorymap.h`).
- `erbium`: [./erbium/README.md](./erbium/README.md) - Hardware abstraction and architecture package for `erbium` under `nuttx/arch/risc-v/src/erbium`, providing 3 header file(s) and 6 source file(s) (including `chip.h`, `erbium_mcode.h`, `erbium_memorymap.h`, `erbium_irq.c`).
- `esp32c2`: [./esp32c2/README.md](./esp32c2/README.md) - Hardware abstraction and architecture package for `esp32c2` under `nuttx/arch/risc-v/src/esp32c2`, providing 2 header file(s) and 4 source file(s) (including `esp_ble.h`, `esp_coex_adapter.h`, `esp_ble.c`, `esp_chip_rev.c`).
- `esp32c3`: [./esp32c3/README.md](./esp32c3/README.md) - Hardware abstraction and architecture package for `esp32c3` under `nuttx/arch/risc-v/src/esp32c3`, providing 4 header file(s) and 6 source file(s) (including `esp_ble.h`, `esp_ble_adapter.h`, `esp_coex_adapter.h`, `esp_wireless.h`).
- `esp32c3-legacy`: [./esp32c3-legacy/README.md](./esp32c3-legacy/README.md) - Hardware abstraction and architecture package for `esp32c3-legacy` (ESP32-C3 Configuration Options; ESP32-C3 Peripheral Support) under `nuttx/arch/risc-v/src/esp32c3-legacy`, providing 51 header file(s) and 61 source file(s) (including `chip.h`, `esp32c3.h`, `esp32c3_adc.h`, `esp32c3_aes.h`).
- `esp32c6`: [./esp32c6/README.md](./esp32c6/README.md) - Hardware abstraction and architecture package for `esp32c6` (ESP32-C6 Configuration Options; Selected ESP32-C6 chip without embedded Flash, an external Flash memory is required.) under `nuttx/arch/risc-v/src/esp32c6`, providing 2 header file(s) and 4 source file(s) (including `esp_ble.h`, `esp_wifi_adapter.h`, `esp_ble.c`, `esp_chip_rev.c`).
- `esp32h2`: [./esp32h2/README.md](./esp32h2/README.md) - Hardware abstraction and architecture package for `esp32h2` under `nuttx/arch/risc-v/src/esp32h2`, providing 1 header file(s) and 2 source file(s) (including `esp_ble.h`, `esp_ble.c`, `esp_chip_rev.c`).
- `esp32p4`: [./esp32p4/README.md](./esp32p4/README.md) - Hardware abstraction and architecture package for `esp32p4` (Maximum Supported ESP32-P4 eFuse Block Revision (eFuse Block Rev v0.99); Cache config) under `nuttx/arch/risc-v/src/esp32p4`, providing 0 header file(s) and 1 source file(s) (including `esp_chip_rev.c`).
- `fe310`: [./fe310/README.md](./fe310/README.md) - Hardware abstraction and architecture package for `fe310` (FE310 Configuration Options; FE310 Peripheral Support) under `nuttx/arch/risc-v/src/fe310`, providing 7 header file(s) and 10 source file(s) (including `chip.h`, `fe310.h`, `fe310_clockconfig.h`, `fe310_config.h`).
- `gd32vw55x`: [./gd32vw55x/README.md](./gd32vw55x/README.md) - Hardware abstraction and architecture package for `gd32vw55x` (GD32VW55x Configuration Options; GD32VW55x Peripheral Support) under `nuttx/arch/risc-v/src/gd32vw55x`, providing 19 header file(s) and 24 source file(s) (including `chip.h`, `gd32vw55x.h`, `gd32vw55x_adc.h`, `gd32vw55x_capture.h`).
- `hpm6000`: [./hpm6000/README.md](./hpm6000/README.md) - Hardware abstraction and architecture package for `hpm6000` (HPM6000 Configuration Options; HPM6000 Peripheral Selection) under `nuttx/arch/risc-v/src/hpm6000`, providing 11 header file(s) and 9 source file(s) (including `chip.h`, `hpm.h`, `hpm_clockconfig.h`, `hpm_config.h`).
- `hpm6750`: [./hpm6750/README.md](./hpm6750/README.md) - Hardware abstraction and architecture package for `hpm6750` (HPM6750 Configuration Options; HPM6750 Peripheral Support) under `nuttx/arch/risc-v/src/hpm6750`, providing 9 header file(s) and 7 source file(s) (including `chip.h`, `hpm6750.h`, `hpm6750_clockconfig.h`, `hpm6750_config.h`).
- `jh7110`: [./jh7110/README.md](./jh7110/README.md) - Hardware abstraction and architecture package for `jh7110` under `nuttx/arch/risc-v/src/jh7110`, providing 3 header file(s) and 7 source file(s) (including `chip.h`, `jh7110_memorymap.h`, `jh7110_mm_init.h`, `jh7110_allocateheap.c`).
- `k210`: [./k210/README.md](./k210/README.md) - Hardware abstraction and architecture package for `k210` (K210 Configuration Options; K210 Peripheral Support) under `nuttx/arch/risc-v/src/k210`, providing 11 header file(s) and 13 source file(s) (including `chip.h`, `k210.h`, `k210_clockconfig.h`, `k210_config.h`).
- `k230`: [./k230/README.md](./k230/README.md) - Hardware abstraction and architecture package for `k230` under `nuttx/arch/risc-v/src/k230`, providing 7 header file(s) and 11 source file(s) (including `chip.h`, `k230_hart.h`, `k230_ipi.h`, `k230_memorymap.h`).
- `litex`: [./litex/README.md](./litex/README.md) - Hardware abstraction and architecture package for `litex` (LITEX Configuration Options; LITEX Peripheral Support) under `nuttx/arch/risc-v/src/litex`, providing 11 header file(s) and 18 source file(s) (including `chip.h`, `litex.h`, `litex_clockconfig.h`, `litex_config.h`).
- `mpfs`: [./mpfs/README.md](./mpfs/README.md) - Hardware abstraction and architecture package for `mpfs` (Polarfire Configuration Options; MPFS Peripheral Support) under `nuttx/arch/risc-v/src/mpfs`, providing 31 header file(s) and 36 source file(s) (including `chip.h`, `mpfs.h`, `mpfs_cache.h`, `mpfs_can.h`).
- `nuttsbi`: [./nuttsbi/README.md](./nuttsbi/README.md) - Hardware abstraction and architecture package for `nuttsbi` under `nuttx/arch/risc-v/src/nuttsbi`, providing 2 header file(s) and 6 source file(s) (including `sbi_internal.h`, `sbi_mcall.h`, `sbi_ipi.c`, `sbi_mcall.c`).
- `qemu-rv`: [./qemu-rv/README.md](./qemu-rv/README.md) - Hardware abstraction and architecture package for `qemu-rv` (QEMU RISC-V Options) under `nuttx/arch/risc-v/src/qemu-rv`, providing 5 header file(s) and 9 source file(s) (including `chip.h`, `qemu_rv_memorymap.h`, `qemu_rv_mm_init.h`, `qemu_rv_rptun.h`).
- `rp23xx-rv`: [./rp23xx-rv/README.md](./rp23xx-rv/README.md) - Hardware abstraction and architecture package for `rp23xx-rv` (RP23XX Configuration Options) under `nuttx/arch/risc-v/src/rp23xx-rv`, providing 21 header file(s) and 26 source file(s) (including `chip.h`, `rp23xx_adc.h`, `rp23xx_clock.h`, `rp23xx_config.h`).
- `rv32m1`: [./rv32m1/README.md](./rv32m1/README.md) - Hardware abstraction and architecture package for `rv32m1` (RV32M1 Configuration Options; RV32M1 Peripheral Support) under `nuttx/arch/risc-v/src/rv32m1`, providing 10 header file(s) and 12 source file(s) (including `chip.h`, `rv32m1.h`, `rv32m1_clockconfig.h`, `rv32m1_gpio.h`).
- `sg2000`: [./sg2000/README.md](./sg2000/README.md) - Hardware abstraction and architecture package for `sg2000` under `nuttx/arch/risc-v/src/sg2000`, providing 3 header file(s) and 7 source file(s) (including `chip.h`, `sg2000_memorymap.h`, `sg2000_mm_init.h`, `sg2000_allocateheap.c`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./ab32vg1/README.md](./ab32vg1/README.md)
- [./allwinner-d1/README.md](./allwinner-d1/README.md)
- [./bl602/README.md](./bl602/README.md)
- [./bl808/README.md](./bl808/README.md)
- [./c906/README.md](./c906/README.md)
- [./common/README.md](./common/README.md)
- [./eic7700x/README.md](./eic7700x/README.md)
- [./erbium/README.md](./erbium/README.md)
- [./esp32c2/README.md](./esp32c2/README.md)
- [./esp32c3/README.md](./esp32c3/README.md)
- [./esp32c3-legacy/README.md](./esp32c3-legacy/README.md)
- [./esp32c6/README.md](./esp32c6/README.md)
- [./esp32h2/README.md](./esp32h2/README.md)
- [./esp32p4/README.md](./esp32p4/README.md)
- [./fe310/README.md](./fe310/README.md)
- [./gd32vw55x/README.md](./gd32vw55x/README.md)
- [./hpm6000/README.md](./hpm6000/README.md)
- [./hpm6750/README.md](./hpm6750/README.md)
- [./jh7110/README.md](./jh7110/README.md)
- [./k210/README.md](./k210/README.md)
- [./k230/README.md](./k230/README.md)
- [./litex/README.md](./litex/README.md)
- [./mpfs/README.md](./mpfs/README.md)
- [./nuttsbi/README.md](./nuttsbi/README.md)
- [./qemu-rv/README.md](./qemu-rv/README.md)
- [./rp23xx-rv/README.md](./rp23xx-rv/README.md)
- [./rv32m1/README.md](./rv32m1/README.md)
- [./sg2000/README.md](./sg2000/README.md)

## Invariants
- `[ab32vg1_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ab32vg1_clockconfig.c:#error]` Compile-time configuration constraint: CONFIG_AB32VG1_SYSCLK_MHZ must divide 240 MHz
- `[ab32vg1_gpio.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ab32vg1_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ab32vg1_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ab32vg1_serial.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[ab32vg1_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ab32vg1_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ab32vg1_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ab32vg1_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ab32vg1_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ab32vg1_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
