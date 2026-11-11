# Semtech SX1301 LoRaWAN Concentrator Driver (`drivers/wireless/lpwan/sx1301`)

## Overview
Implements the SPI character driver for the Semtech SX1301 multi-channel LoRaWAN baseband concentrator (`sx1301.c`), including banked register access (`sx1301_reg.c`), regional channel plan tables (`sx1301_region.c`), and AGC/arbiter MCU firmware images (`sx1301_fw.c`).

## Interface
- `[sx1301.c:sx1301_register]` - Resets and probes the SX1301 concentrator over SPI and registers a character device (e.g., `/dev/sx1301`) supporting `WLIOC_*` and SX1301-specific ioctls.
- `[sx1301_reg.c:sx1301_reg_probe]`, `[sx1301_reg.c:sx1301_reg_write]`, `[sx1301_reg.c:sx1301_reg_read]`, `[sx1301_reg.c:sx1301_reg_wrburst]`, `[sx1301_reg.c:sx1301_reg_rdburst]`, `[sx1301_reg.c:sx1301_reg_setbit]`, `[sx1301_reg.c:sx1301_reg_write13s]` - Banked SPI register and burst memory access helpers.
- `[sx1301_region.c:sx1301_region_count]`, `[sx1301_region.c:sx1301_region_byname]`, `[sx1301_region.c:sx1301_region_getinfo]`, `[sx1301_region.c:sx1301_region_apply]` - Looks up and applies regional LoRaWAN IF/RF frequency plans (`EU868`, `US915`, `AS923`, etc.).
- `[sx1301_fw.c:g_sx1301_agc_fw]`, `[sx1301_fw.c:g_sx1301_arb_fw]`, `[sx1301_fw.c:g_sx1301_cal_fw]` - Embedded 8192-byte MCU firmware images for calibration, AGC, and packet arbitration.

## Invariants
- `[sx1301.c:sx1301_register]` asserts `DEBUGASSERT(devpath != NULL && spi != NULL && lower != NULL)` and `DEBUGASSERT(lower->reset != NULL)`.

## Side Effects
- Pulses the hardware reset line (`lower->reset`), uploads MCU firmware bursts over SPI (`sx1301_reg_wrburst`), configures front-end SX1255/SX1257 radios, and registers a character device via `register_driver` synchronized by `nxmutex_lock(&priv->lock)`.

## Verification
- Run: `make test`
