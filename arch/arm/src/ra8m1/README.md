# ra8m1 (`nuttx/arch/arm/src/ra8m1`)

## Overview
Hardware abstraction and architecture package for `ra8m1` (RA Configuration Options; RA8M1 Peripheral Support) under `nuttx/arch/arm/src/ra8m1`, providing 10 header file(s) and 14 source file(s) (including `chip.h`, `ra_clockconfig.h`, `ra_dtc.h`, `ra_gpio.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/ra8m1/hardware`, providing 13 header file(s) and 0 source file(s) (including `ra8m1_dtc.h`, `ra8m1_elc.h`, `ra8m1_fcache.h`, `ra8m1_gpio.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV8M_ICACHE_LINESIZE]`
- `[chip.h:ARMV8M_DCACHE_LINESIZE]`
- `[ra_clockconfig.h:ra_clockconfig]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_MOCO]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_HOCO]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_MOSC]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_PLL1P]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_PLL1Q]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_PLL1R]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_PLL2P]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_PLL2Q]`
- `[ra_clockconfig.h:RA_SCICLK_SRC_PLL2R]`
- `[ra_clockconfig.h:RA_USE_SCICLK]`
- `[ra_clockconfig.h:RA_USE_PLL1]`
- `[ra_dtc.h:ra8m1_dtc_vectbl_entry]`
- `[ra_dtc.h:ra8m1_dtc_vectbl_set]`
- `[ra_dtc.h:ra8m1_dtc_transfer_info]`
- `[ra_dtc.h:ra_dtc_initialize]`
- `[ra_dtc.h:ra_dtc_configure]`
- `[ra_dtc.h:ra_dtc_enable]`
- `[ra_dtc.h:ra_dtc_disable]`
- `[ra_dtc.h:dtc_transfer_info_s]`
- `[ra_gpio.h:ra_configgpio]`
- `[ra_gpio.h:ra_gpiowrite]`
- `[ra_gpio.h:ra_gpioread]`
- `[ra_gpio.h:gpio_pinset_t]`
- `[ra_gpt.h:ra_gpt_timer_initialize]`
- `[ra_gpt.h:RA_GPT32_FIRST]`
- `[ra_gpt.h:RA_GPT32_LAST]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[ra_clockconfig.h:#error]` Compile-time guard: board.h must define BOARD_HOCO_FREQUENCY
- `[ra_dtc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ra_gpt.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ra_icu.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[ra_iic_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ra_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ra_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ra_lowputc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ra_lowputc.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting
- `[ra_option_setting.c:#error]` Compile-time configuration constraint: board.h must define BOARD_OFS0_IWDT_AUTOSTART
- `[ra_sci_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ra_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[ra_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ra_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ra_clockconfig.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[ra_clockconfig.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[ra_clockconfig.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[ra_dtc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ra_dtc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ra_dtc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ra_dtc.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[ra_dtc.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[ra_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ra_gpio.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)

## Verification
- Run: `make test`
