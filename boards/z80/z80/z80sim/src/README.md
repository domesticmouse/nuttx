# `z80sim/src` Component (`boards/z80/z80/z80sim/src`)

## Overview
Board-level C implementation (`src`) for `z80sim` (`z80/z80`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[z80_irq.c:z80sim_timerisr]` Public function `z80sim_timerisr()`
- `[z80_irq.c:up_irqinitialize]` Public function `up_irqinitialize()`
- `[z80_lowputc.c]` Translation unit `z80_lowputc.c`
- `[z80_serial.c:z80_serial_initialize]` Public function `z80_serial_initialize()`
- `[z80_serial.c:up_putc]` Public function `up_putc()`
- `[z80_timerisr.c:z80sim_timerisr]` Public function `z80sim_timerisr()`
- `[z80_timerisr.c:up_timer_initialize]` Public function `up_timer_initialize()`

## Invariants
- `[z80_serial.c:z80_serial_initialize]` Validates preconditions and returns `-ENOTTY` on failure

## Side Effects
- `[z80_irq.c:z80sim_timerisr]` Modifies interrupt controller or critical-section state
- `[z80_serial.c:z80_serial_initialize]` Initializes/registers kernel devices or filesystems (`uart_register()`)

## Verification
- Run: `./tools/configure.sh z80sim:nsh && make`
