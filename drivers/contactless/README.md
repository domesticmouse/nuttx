# Contactless / NFC Drivers (`drivers/contactless`)

## Overview
Provides SPI character drivers for 13.56 MHz contactless RFID/NFC transceiver ICs, supporting the NXP MFRC522 proximity coupling device and the NXP PN532 NFC controller.

## Interface
- `mfrc522.c:mfrc522_register`, `mfrc522.h:mfrc522_dev_s` - Allocates and registers an MFRC522 contactless reader character device on an SPI bus.
- `mfrc522.h:mfrc522_set_config`, `mfrc522.c:mfrc522_selftest`, `mfrc522.c:mfrc522_picc_request_a`, `mfrc522.c:mfrc522_picc_select` - Configures SPI parameters and executes ISO/IEC 14443A PICC polling, anti-collision, and MIFARE transceive sequences.
- `pn532.c:pn532_register`, `pn532.h:pn532_dev_s`, `pn532.h:pn532_frame` - Allocates and registers a PN532 NFC character device on an SPI bus.
- `pn532.c:pn532_sam_config`, `pn532.c:pn532_get_fw_version`, `pn532.c:pn532_read_passive_target_id`, `pn532.c:pn532_read_passive_data`, `pn532.c:pn532_write_passive_data`, `pn532.c:pn532_set_rf_config`, `pn532.c:pn532_write_gpio` - Executes PN532 host controller frames for SAM configuration, passive target detection, data exchange, RF tuning, and GPIO control.

## Invariants
- Open, close, read, write, and `ioctl` file operations assert `inode->i_private != NULL` (`mfrc522.c:mfrc522_register`, `pn532.c:pn532_register`).
- `pn532.c:pn532_write_passive_data` asserts `conf->data_size <= 16 - 2` to fit within a single MIFARE block frame.

## Side Effects
- Locks the SPI bus (`SPI_LOCK`), asserts chip select (`SPI_SELECT`), and performs SPI frame transfers (`SPI_SEND`, `SPI_SNDBLOCK`, `SPI_RECVBLOCK`) (`mfrc522.c:mfrc522_register`, `pn532.c:pn532_write_frame`).
- Registers character devices in the VFS via `register_driver` and allocates driver state on the heap via `kmm_malloc` (`mfrc522.c:mfrc522_register`, `pn532.c:pn532_register`).
- Attaches GPIO interrupt callbacks and schedules work queue tasks (`work_queue`) when `CONFIG_PN532_USE_IRQ_FLOW_CONTROL` is enabled (`pn532.c:pn532_register`).

## Verification
- Run: `make test`
