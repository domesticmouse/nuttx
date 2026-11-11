# NuttX Radio Frequency (RF) Peripherals (`include/nuttx/rf`)

## Overview
Defines character driver interfaces, ioctl commands, and chip registration functions for Radio Frequency (`RF`) front-end components such as digital step attenuators.

## Interface
- `ioctl.h:RFIOC_SETATT` - RF character device ioctl command to configure attenuation levels.
- `attenuator.h:attenuator_control` - Structure describing target channel and attenuation setting (in dB) for RF attenuator ioctls.
- `dat-31r5-sp.h:dat31r5sp_register` - Registration entry point for the Mini-Circuits DAT-31R5-SP+ SPI digital step attenuator driver.

## Invariants
- Callers of `dat-31r5-sp.h:dat31r5sp_register` must pass a valid initialized `struct spi_dev_s` instance and a unique SPI device ID (`spidev_id`) for chip-select control.

## Side Effects
- `dat-31r5-sp.h:dat31r5sp_register` creates an RF character device node in `/dev` and configures initial SPI bus parameters.
- Issuing `ioctl.h:RFIOC_SETATT` triggers SPI transfers to latch a new attenuation word into the hardware attenuator.

## Verification
- Run: `make test`
