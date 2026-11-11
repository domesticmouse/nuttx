# Contactless / NFC Subsystem Headers (`include/nuttx/contactless`)

## Overview
Defines the shared `ioctl` commands, MIFARE/ISO14443A card data structures, and SPI driver registration interfaces for contactless/NFC reader chips (MFRC522 and PN532).

## Interface
- `ioctl.h:MFRC522IOC_GET_PICC_UID`, `ioctl.h:MFRC522IOC_GET_STATE`, `ioctl.h:PN532IOC_SET_SAM_CONF`, `ioctl.h:PN532IOC_READ_PASSIVE`, `ioctl.h:PN532IOC_SET_RF_CONF`, `ioctl.h:PN532IOC_GET_TAG_ID`, `ioctl.h:CLIOC_READ_MIFARE_DATA`, `ioctl.h:CLIOC_WRITE_MIFARE_DATA` - Contactless subsystem `ioctl` commands.
- `ioctl.h:picc_uid_s`, `ioctl.h:picc_cardid_e`, `ioctl.h:mifare_tag_data_s` - Proximity Integrated Circuit Card (PICC) UID, card type enum, and MIFARE block transfer structures.
- `mfrc522.h:mfrc522_state_e`, `mfrc522.h:mfrc522_dev_s`, `mfrc522.h:mfrc522_register` - NXP MFRC522 contactless reader state enumeration and SPI character driver registration.
- `pn532.h:pn532_state_e`, `pn532.h:pn532_config_s`, `pn532.h:pn_sam_settings_s`, `pn532.h:pn_rf_config_s`, `pn532.h:pn_mifare_tag_data_s`, `pn532.h:pn532_register` - NXP PN532 NFC controller board configuration, SAM/RF settings, and SPI driver registration.

## Invariants
- `ioctl.h:picc_uid_s` stores UIDs up to `10` bytes (`uid_data[10]`), and `ioctl.h:mifare_tag_data_s` transfers fixed `16`-byte MIFARE blocks (`data[16]`).
- `pn532.h:pn532_config_s` callbacks (`reset`, `select`, `irqattach`) must be provided by board logic to control chip-select, reset, and IRQ lines.

## Side Effects
- `mfrc522.h:mfrc522_register` and `pn532.h:pn532_register` allocate driver state, initialize the SPI-attached NFC transceiver, attach interrupts, and register character device nodes in the VFS.

## Verification
- Run: `make test`
