# STMicroelectronics SPIRIT1 Control Library (`drivers/wireless/spirit/lib`)

## Overview
Implements the hardware control library for STMicroelectronics SPIRIT1 sub-1 GHz RF transceivers, providing SPI register and FIFO access (`spirit_spi.c`), RF analog/digital front-end setup (`spirit_radio.c`, `spirit_calibration.c`, `spirit_management.c`, `spirit_directrf.c`), packet handlers for Basic, STack, and M-Bus frames (`spirit_pktcommon.c`, `spirit_pktbasic.c`, `spirit_pktstack.c`, `spirit_pktmbus.c`), CSMA/CA engine (`spirit_csma.c`), AES-128 hardware encryption (`spirit_aes.c`), quality indicators (`spirit_qi.c`), timers (`spirit_timer.c`), interrupts (`spirit_irq.c`), linear FIFOs (`spirit_linearfifo.c`), and GPIO/general configuration (`spirit_gpio.c`, `spirit_general.c`).

## Interface
- `[spirit_spi.c:spirit_reg_read]`, `[spirit_spi.c:spirit_reg_write]`, `[spirit_spi.c:spirit_reg_modify]`, `[spirit_spi.c:spirit_command]`, `[spirit_spi.c:spirit_fifo_read]`, `[spirit_spi.c:spirit_fifo_write]`, `[spirit_spi.c:spirit_update_status]`, `[spirit_spi.c:spirit_waitstatus]` - Low-level SPI bus transactions and MC_STATE polling.
- `[spirit_radio.c:spirit_radio_initialize]`, `[spirit_radio.c:spirit_radio_get_setup]`, `[spirit_radio.c:spirit_radio_set_xtalflag]`, `[spirit_radio.c:spirit_radio_search_wcp]`, `[spirit_radio.c:spirit_radio_get_synthword]`, `[spirit_radio.c:spirit_radio_set_synthword]`, `[spirit_radio.c:spirit_radio_set_band]`, `[spirit_radio.c:spirit_radio_set_channel]` - RF frequency synthesizer, modulation, and PA power configuration.
- `[spirit_pktbasic.c:spirit_pktbasic_initialize]`, `[spirit_pktstack.c:spirit_pktstack_initialize]`, `[spirit_pktmbus.c:spirit_pktmbus_initialize]`, `[spirit_pktcommon.c:spirit_pktcommon_set_controllen]` - Packet framing, preamble/sync/CRC, and address filtering configuration.
- `[spirit_csma.c:spirit_csma_initialize]`, `[spirit_csma.c:spirit_csma_enable]`, `[spirit_irq.c:spirit_irq_disable_all]`, `[spirit_irq.c:spirit_irq_set_mask]`, `[spirit_irq.c:spirit_irq_enable]`, `[spirit_irq.c:spirit_irq_get_pending]`, `[spirit_irq.c:spirit_irq_clr_pending]`, `[spirit_linearfifo.c:spirit_fifo_get_rxcount]`, `[spirit_linearfifo.c:spirit_fifo_get_txcount]` - CSMA/CA, IRQ mask/status, and FIFO byte count operations.
- `[spirit_aes.c:spirit_aes_enable]`, `[spirit_aes.c:spirit_aes_encrypt]`, `[spirit_aes.c:spirit_aes_decrypt]`, `[spirit_calibration.c:spirit_calib_enable_rco]`, `[spirit_calibration.c:spirit_calib_enable_vco]`, `[spirit_directrf.c:spirit_directrf_set_rxmode]`, `[spirit_directrf.c:spirit_directrf_set_txmode]`, `[spirit_general.c:spirit_general_get_partnumber]`, `[spirit_general.c:spirit_general_get_version]`, `[spirit_gpio.c:spirit_gpio_initialize]`, `[spirit_management.c:spirit_managment_wavco_calibration]`, `[spirit_qi.c:spirit_qi_get_rssi]`, `[spirit_qi.c:spirit_qi_get_lqi]`, `[spirit_timer.c:spirit_timer_setup_rxtimeout]`, `[spirit_timer.c:spirit_timer_setup_wakeuptimer]` - AES engine, VCO/RCO calibration, quality indicators, GPIO, and RX/wakeup timers.

## Invariants
- `[spirit_spi.c:spirit_reg_read]` and all SPI accessors assert `DEBUGASSERT(spirit != NULL)`.
- Library functions validate all enum and numeric arguments using `DEBUGASSERT(IS_*(...))` macros (e.g., `IS_SPIRIT_FUNCTIONAL_STATE`, `IS_FREQUENCY_BAND`, `IS_MODULATION_SELECTED`, `IS_DATARATE`, `IS_FIFO_THR`, `IS_SPIRIT_IRQ_LIST`).

## Side Effects
- `[spirit_spi.c:spirit_reg_read]`, `[spirit_spi.c:spirit_reg_write]`, `[spirit_spi.c:spirit_command]`, `[spirit_spi.c:spirit_fifo_read]`, and `[spirit_spi.c:spirit_fifo_write]` acquire exclusive access to `spirit->spi` (`SPI_LOCK`), assert chip-select (`SPI_SELECT`), exchange 2-byte status headers and register/FIFO payloads (`SPI_EXCHANGE`), and update `spirit->state` with the returned 16-bit `MC_STATE` word.

## Verification
- Run: `make test`
