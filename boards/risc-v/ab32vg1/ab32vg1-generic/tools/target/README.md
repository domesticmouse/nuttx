# `ab32vg1-generic/tools/target` Component (`boards/risc-v/ab32vg1/ab32vg1-generic/tools/target`)

## Overview
Board support component `tools/target` for `ab32vg1-generic` (`risc-v/ab32vg1`), containing 6 source/script file(s) (`boot.c, spiflash.c, stub.c, stub.h`).

## Interface
- `[stub.h:STUB_VERSION]` Hardware/board configuration macros (`STUB_VERSION`, `STUB_REQ_SYNC`, `STUB_RSP_SYNC`, `STUB_MAXDATA`, `STUB_CMD_INFO`, `STUB_CMD_READ` (+11 more))
- `[target.h:sf_init]` Public declaration `sf_init()`
- `[target.h:sf_readid]` Public declaration `sf_readid()`
- `[target.h:sf_status]` Public declaration `sf_status()`
- `[target.h:sf_read]` Public declaration `sf_read()`
- `[target.h:sf_erase]` Public declaration `sf_erase()`
- `[target.h:sf_program]` Public declaration `sf_program()`
- `[target.h:uart_init]` Public declaration `uart_init()`
- `[target.h:uart_putc]` Public declaration `uart_putc()`
- `[target.h:uart_puts]` Public declaration `uart_puts()`
- `[target.h:uart_getc]` Public declaration `uart_getc()`
- `[target.h:uart_trygetc]` Public declaration `uart_trygetc()`
- `[target.h:crc32_update]` Public declaration `crc32_update()`
- `[target.h:crc16_update]` Public declaration `crc16_update()`
- `[target.h:img_seg_s]` Type definition `img_seg_s`
- `[target.h:img_table_s]` Type definition `img_table_s`
- `[target.h:SFR]` Hardware/board configuration macros (`SFR`, `FUNCMCON0`, `UART0CON`, `UART0CPND`, `UART0BAUD`, `UART0DATA` (+34 more))
- `[boot.c:boot_main]` Public function `boot_main()`
- `[spiflash.c:sf_init]` Public function `sf_init()`
- `[spiflash.c:sf_readid]` Public function `sf_readid()`
- `[spiflash.c:sf_status]` Public function `sf_status()`
- `[spiflash.c:sf_read]` Public function `sf_read()`
- `[spiflash.c:sf_erase]` Public function `sf_erase()`
- `[spiflash.c:sf_program]` Public function `sf_program()`
- `[stub.c:stub_main]` Public function `stub_main()`
- *(+7 additional symbols across 6 files)*

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ab32vg1-generic:nsh && make`
