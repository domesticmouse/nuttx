# STMicroelectronics SPIRIT1 Library Headers (`drivers/wireless/spirit/include`)

## Overview
Header files defining register addresses (`spirit_regs.h`), configuration constants (`spirit_config.h`, `spirit_types.h`, `spirit_commands.h`), parameter validation macros, and public API prototypes for the STMicroelectronics SPIRIT1 sub-1 GHz RF transceiver library.

## Interface
- `[spirit_spi.h:spirit_reg_read]`, `[spirit_spi.h:spirit_reg_write]`, `[spirit_spi.h:spirit_reg_modify]`, `[spirit_spi.h:spirit_command]`, `[spirit_spi.h:spirit_fifo_read]`, `[spirit_spi.h:spirit_fifo_write]`, `[spirit_spi.h:spirit_update_status]`, `[spirit_spi.h:spirit_waitstatus]` - SPI register, command strobe, FIFO, and status polling prototypes.
- `[spirit_radio.h:spirit_radio_initialize]`, `[spirit_radio.h:spirit_radio_set_band]`, `[spirit_radio.h:spirit_radio_set_channel]`, `[spirit_radio.h:spirit_radio_set_palelleveldBm]`, `[spirit_management.h:spirit_managment_wavco_calibration]`, `[spirit_management.h:spirit_management_txstrobe]`, `[spirit_management.h:spirit_management_rxstrobe]` - RF synthesizer, PA power, and state management declarations.
- `[spirit_pktcommon.h:spirit_pktcommon_set_controllen]`, `[spirit_pktbasic.h:spirit_pktbasic_initialize]`, `[spirit_pktstack.h:spirit_pktstack_initialize]`, `[spirit_pktmbus.h:spirit_pktmbus_initialize]` - Basic, STack (6LoWPAN), and Wireless M-Bus packet handler declarations.
- `[spirit_csma.h:spirit_csma_initialize]`, `[spirit_csma.h:spirit_csma_enable]`, `[spirit_irq.h:spirit_irq_set_mask]`, `[spirit_irq.h:spirit_irq_get_pending]`, `[spirit_linearfifo.h:spirit_fifo_get_rxcount]`, `[spirit_linearfifo.h:spirit_fifo_get_txcount]`, `[spirit_qi.h:spirit_qi_get_rssi]`, `[spirit_qi.h:spirit_qi_get_lqi]`, `[spirit_timer.h:spirit_timer_setup_rxtimeout]`, `[spirit_aes.h:spirit_aes_encrypt]`, `[spirit_calibration.h:spirit_calib_enable_vco]`, `[spirit_directrf.h:spirit_directrf_set_rxmode]`, `[spirit_general.h:SPIRIT_GENERAL_LIBVERSION]`, `[spirit_gpio.h:spirit_gpio_initialize]` - Peripheral block API declarations and `IS_*` parameter range check macros.
- `[spirit_types.h:spirit_library_s]`, `[spirit_types.h:spirit_status_s]`, `[spirit_regs.h:ANA_FUNC_CONF1_BASE]` - Core state structures and hardware register address definitions.

## Invariants
- Parameter validation macros (`[spirit_types.h:IS_SPIRIT_FUNCTIONAL_STATE]`, `[spirit_calibration.h:IS_VCO_WIN]`, `[spirit_csma.h:IS_CCA_PERIOD]`, `[spirit_gpio.h:IS_SPIRIT_GPIO]`, `[spirit_linearfifo.h:IS_FIFO_THR]`) define the legal value domains enforced via `DEBUGASSERT` across `drivers/wireless/spirit/lib`.

## Side Effects
- None (header-only declarations and inline/macro definitions).

## Verification
- Run: `make test`
