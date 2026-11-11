# Semtech SX126x LoRa and GFSK Transceiver Driver (`drivers/wireless/lpwan/sx126x`)

## Overview
Implements the SPI character driver (`sx126x.c`, `sx126x.h`) for Semtech SX1261/SX1262/SX1268 sub-GHz LoRa and GFSK RF transceivers.

## Interface
- `[sx126x.c:sx126x_register]` - Allocates an SX126x device instance, attaches DIO1 interrupt handling, and registers the character device (`devpath`) in the VFS.
- `[sx126x.c:sx126x_convert_freq_in_hz_to_pll_step]` - Converts a frequency in Hz into SX126x 32-bit PLL step units.
- `[sx126x.h:SX126X_MAX_DEVICES]`, `[sx126x.h:SX126X_SPI_SPEED]`, `[sx126x.h:SX126X_DEFAULT_LORA_SF]`, `[sx126x.h:SX126X_DEFAULT_LORA_BW]` - Default driver configuration constants and command opcodes.

## Invariants
- `[sx126x.c:sx126x_get_freq]` and `[sx126x.c:sx126x_set_freq]` assert `DEBUGASSERT(freq_ptr != NULL)` and `[sx126x.c:sx126x_read]` asserts `DEBUGASSERT(ptr != NULL)`.

## Side Effects
- Registers a character device via `register_driver`, toggles hardware reset and polls the BUSY line via `lower->reset` and `lower->busy_read`, performs SPI opcode/register/buffer transfers (`SPI_EXCHANGE`), attaches DIO1 interrupts (`lower->irq1_attach`), and wakes blocked readers/pollers via `nxsem_post` and `poll_notify`.

## Verification
- Run: `make test`
