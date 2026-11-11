# Semtech SX127x LoRa and FSK/OOK Transceiver Driver (`drivers/wireless/lpwan/sx127x`)

## Overview
Implements the character driver (`sx127x.c`, `sx127x.h`) for Semtech SX1272/SX1276/SX1277/SX1278/SX1279 sub-1 GHz LoRa and FSK/OOK RF transceivers over SPI.

## Interface
- `[sx127x.c:sx127x_register]` - Initializes an SX127x SPI device, attaches DIO0..DIO5 interrupt handlers, and registers the `/dev/sx127x` (or custom path) character device.
- `[sx127x.h:SX127X_R_REGISTER]`, `[sx127x.h:SX127X_W_REGISTER]`, `[sx127x.h:SX127X_CMN_FIFO]`, `[sx127x.h:SX127X_CMN_OPMODE]` - Register addresses, bitmasks, and modulation constants for Common, FSK/OOK, and LoRa register pages.

## Invariants
- `[sx127x.c:sx127x_open]`, `[sx127x.c:sx127x_close]`, `[sx127x.c:sx127x_read]`, `[sx127x.c:sx127x_write]`, and `[sx127x.c:sx127x_ioctl]` assert `DEBUGASSERT(inode->i_private)`.

## Side Effects
- Registers a character device via `register_driver`.
- Locks the SPI bus (`SPI_LOCK`), toggles chip-select (`SPI_SELECT`), and performs single-byte and burst FIFO transfers (`SPI_SEND`, `SPI_SNDBLOCK`, `SPI_RECVBLOCK`) to configure frequency, PA boost, spreading factor, bandwidth, coding rate, and opmode.
- Attaches DIO0..DIO5 hardware interrupts via `lower->irq0_attach`..`irq5_attach`, schedules interrupt processing on `HPWORK` (`work_queue`), buffers received frames in a software RX FIFO, and wakes waiting readers/pollers via `nxsem_post` and `poll_notify`.

## Verification
- Run: `make test`
