# RF Attenuator Drivers (`drivers/rf`)

## Overview
Provides character drivers for Radio Frequency (RF) signal conditioning hardware, specifically the Mini-Circuits DAT-31R5-SP+ SPI-controlled digital step attenuator.

## Interface
- `[dat-31r5-sp.c:dat31r5sp_register]` - Registers a `/dev/attenuatorN` character device for a Mini-Circuits DAT-31R5-SP+ digital step attenuator (`[dat-31r5-sp.c:struct dat31r5sp_dev_s]`, `[dat-31r5-sp.c:CONFIG_RF_DAT31R5SP]`).

## Invariants
- Attenuation values passed via `WLIOC_SETRADIOFREQ` / `RFIOC_SETATTENUATION` or `write` must lie between `0` and `31.5 dB` (`b16_t`), returning `-EINVAL` otherwise (`[dat-31r5-sp.c:dat31r5sp_set_attenuation]`).

## Side Effects
- Registers a VFS character driver via `[dat-31r5-sp.c:register_driver]` and locks/drives the SPI bus (`SPI_LOCK`, `[dat-31r5-sp.c:SPI_SEND]`, `SPI_SELECT`) to latch 6-bit attenuation control words.

## Verification
- Run: `make test`
