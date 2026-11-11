# STMicroelectronics SPIRIT1 Sub-1 GHz RF Subsystem (`drivers/wireless/spirit`)

## Overview
Groups the STMicroelectronics SPIRIT1 sub-1 GHz low-power RF transceiver control library, public headers, and NuttX 6LoWPAN/IEEE 802.15.4 network device driver.

## Subdirectories & Boundaries
- `drivers`: [./drivers/README.md](./drivers/README.md) - NuttX 6LoWPAN network device driver (`spirit_netdev.c`) for SPIRIT1 transceivers.
- `include`: [./include/README.md](./include/README.md) - Register definitions, types, validation macros, and function prototypes for the SPIRIT1 library.
- `lib`: [./lib/README.md](./lib/README.md) - SPIRIT1 SPI register/FIFO access, radio synthesizer, packet handler, CSMA, AES, IRQ, and timer control routines.
