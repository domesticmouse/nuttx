# Microchip RN2483 / RN2903 LoRa Transceiver Driver (`drivers/wireless/lpwan/rn2xx3`)

## Overview
Implements a character driver (`rn2xx3.c`) for Microchip RN2483 and RN2903 LoRa/FSK radio modules controlled via an ASCII command interface over a UART file descriptor.

## Interface
- `[rn2xx3.c:rn2xx3_register]` - Initializes an RN2xx3 device instance attached to the specified UART device path (`uartpath`) and registers a character device (`devpath`) supporting `WLIOC_*` radio ioctls and raw packet read/write.

## Invariants
- `[rn2xx3.c:rn2xx3_set_mod]` asserts `DEBUGASSERT(mod == RN2XX3_MOD_LORA || mod == RN2XX3_MOD_FSK)`.
- Internal getter helpers assert non-null output pointers (`DEBUGASSERT(snr != NULL)`, `DEBUGASSERT(freq != NULL)`, `DEBUGASSERT(bw != NULL)`, `DEBUGASSERT(txp != NULL)`).

## Side Effects
- Opens the underlying UART character device via `file_open(&priv->uart, priv->uartpath, O_RDWR | O_CLOEXEC)`, transmits ASCII `sys`/`radio`/`mac` commands (`file_write`), parses responses (`file_read`), and registers the radio character device via `register_driver` under `nxmutex_lock(&priv->lock)`.

## Verification
- Run: `make test`
