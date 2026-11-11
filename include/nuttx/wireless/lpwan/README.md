# NuttX Low-Power Wide-Area Network (LPWAN) Subsystem (`include/nuttx/wireless/lpwan`)

## Overview
Provides character driver interfaces, modulation/packet structures, and `ioctl` commands for Low-Power Wide-Area Network (`LPWAN`) and LoRa transceivers and concentrator gateways, including Semtech SX126x, SX127x, SX1301, and Microchip RN2xx3 modules.

## Interface
- `sx127x.h:sx127x_lower_s`, `sx127x.h:sx127x_read_hdr_s`, `sx127x.h:sx127x_modulation_e`, `sx127x.h:sx127x_lora_bw_e`, `sx127x.h:sx127x_lora_sf_e`, `sx127x.h:sx127x_lora_cr_e`, `sx127x.h:sx127x_register`, `sx127x.h:SX127XIOC_RSSIGET`, `sx127x.h:SX127XIOC_MODULATIONSET` - Semtech SX127x LoRa/FSK/OOK transceiver driver interface and device-specific `ioctl` commands.
- `sx126x.h:sx126x_lower_s`, `sx126x.h:sx126x_packet_type_e`, `sx126x.h:sx126x_lora_sf_e`, `sx126x.h:sx126x_lora_bw_e`, `sx126x.h:sx126x_lora_cr_e`, `sx126x.h:sx126x_register`, `sx126x.h:SX126XIOC_PACKETTYPESET`, `sx126x.h:SX126XIOC_LORACONFIGSET` - Semtech SX1261/SX1262/SX1268 sub-GHz LoRa transceiver driver interface.
- `sx1301.h:sx1301_lower_s`, `sx1301.h:sx1301_register`, `lora_gw.h:lora_gw_rxpkt_s`, `lora_gw.h:lora_gw_txpkt_s`, `lora_gw.h:lora_gw_status_s`, `lora_gw.h:lora_gw_chaninfo_s`, `lora_gw.h:lora_gw_regioninfo_s` - Multi-channel LoRa concentrator gateway structures and Semtech SX1301 driver registration.
- `rn2xx3.h:rn2xx3_mod_e`, `rn2xx3.h:rn2xx3_cr_e`, `rn2xx3.h:rn2xx3_register` - Microchip RN2483/RN2903 UART-attached LoRaWAN transceiver driver registration.

## Invariants
- Board lower-half descriptors (`sx127x.h:sx127x_lower_s`, `sx126x.h:sx126x_lower_s`, `sx1301.h:sx1301_lower_s`) must remain valid for the lifetime of the registered `/dev/lpwan*` or `/dev/sx*` device and provide valid DIO/IRQ attachment callbacks.

## Side Effects
- `sx127x.h:sx127x_register`, `sx126x.h:sx126x_register`, `sx1301.h:sx1301_register`, and `rn2xx3.h:rn2xx3_register` reset the radio hardware, configure SPI/UART communication, attach DIO interrupt handlers, and register character device nodes in `/dev`.

## Verification
- Run: `make test`
