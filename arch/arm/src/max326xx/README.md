# max326xx (`nuttx/arch/arm/src/max326xx`)

## Overview
Hardware abstraction and architecture package for `max326xx` (Maxim Integrate MAX326xx Configuration Options; MAX32xx Peripheral Selection) under `nuttx/arch/arm/src/max326xx`, providing 16 header file(s) and 0 source file(s) (including `chip.h`, `max326_clockconfig.h`, `max326_config.h`, `max326_dma.h`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/arm/src/max326xx/common`, providing 0 header file(s) and 8 source file(s) (including `max326_clrpend.c`, `max326_idle.c`, `max326_irq.c`, `max326_mpuinit.c`).
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/max326xx/hardware`, providing 30 header file(s) and 0 source file(s) (including `max32620_30_memorymap.h`, `max32660_flc.h`, `max32660_gcr.h`, `max32660_gpio.h`).
- `max32620_30`: [./max32620_30/README.md](./max32620_30/README.md) - Hardware abstraction and architecture package for `max32620_30` under `nuttx/arch/arm/src/max326xx/max32620_30`, providing 1 header file(s) and 0 source file(s) (including `max32620_30_clockconfig.h`).
- `max32660`: [./max32660/README.md](./max32660/README.md) - Hardware abstraction and architecture package for `max32660` under `nuttx/arch/arm/src/max326xx/max32660`, providing 4 header file(s) and 10 source file(s) (including `max32660_clockconfig.h`, `max32660_dma.h`, `max32660_gpio.h`, `max32660_periphclks.h`).
- `max32690`: [./max32690/README.md](./max32690/README.md) - Hardware abstraction and architecture package for `max32690` under `nuttx/arch/arm/src/max326xx/max32690`, providing 2 header file(s) and 3 source file(s) (including `max32690_gpio.h`, `max32690_periphclks.h`, `max32690_gpio.c`, `max32690_gpioirq.c`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[max326_clockconfig.h:max326_clockconfig]`
- `[max326_clockconfig.h:max326_hfio_frequency]`
- `[max326_clockconfig.h:max326_cpu_frequency]`
- `[max326_clockconfig.h:max326_pclk_frequency]`
- `[max326_config.h:HAVE_UART_DEVICE]`
- `[max326_config.h:HAVE_UART_CONSOLE]`
- `[max326_icc.h:max326_icc_enable]`
- `[max326_icc.h:max326_icc_invalidate]`
- `[max326_irq.h:max326_clrpend]`
- `[max326_lowputc.h:max326_lowsetup]`
- `[max326_lowputc.h:max326_uart_configure]`
- `[max326_lowputc.h:max326_uart_disable]`
- `[max326_lowputc.h:uart_config_s]`
- `[max326_mpuinit.h:max326_mpuinitialize]`
- `[max326_mpuinit.h:max326_mpu_uheap]`
- `[max326_rtc.h:max326_rtc_setalarm]`
- `[max326_rtc.h:max326_rtc_rdalarm]`
- `[max326_rtc.h:max326_rtc_cancelalarm]`
- `[max326_rtc.h:max326_rtc_lowerhalf]`
- `[max326_serial.h:max326_earlyserialinit]`
- `[max326_spim.h:max326_spibus_initialize]`
- `[max326_spim.h:max326_spi0select]`
- `[max326_spim.h:max326_spi0status]`
- `[max326_spim.h:max326_spi0cmddata]`
- `[max326_spim.h:max326_spi1select]`
- `[max326_spim.h:max326_spi1status]`
- `[max326_spim.h:max326_spi1cmddata]`
- `[max326_spim.h:max326_spi2select]`
- `[max326_spim.h:max326_spi2status]`
- [./common/README.md](./common/README.md)
- [./hardware/README.md](./hardware/README.md)
- [./max32620_30/README.md](./max32620_30/README.md)
- [./max32660/README.md](./max32660/README.md)
- [./max32690/README.md](./max32690/README.md)

## Invariants
- `[max326_clockconfig.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_gpio.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_periphclks.h:#error]` Compile-time guard: Unsupported MAX326XX family

## Side Effects
- None

## Verification
- Run: `make test`
