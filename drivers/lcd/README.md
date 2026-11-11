# LCD, OLED, and Segment Display Drivers (`drivers/lcd`)

## Overview
Provides the NuttX LCD character driver (`lcd_dev`), LCD-to-framebuffer bridge (`lcd_framebuffer`), SPI LCD interface wrapper (`lcddrv_spiif`), and hardware controller drivers for TFT/OLED graphic displays, e-ink panels, HDMI transmitters, and alphanumeric/segment displays over SPI, I2C, and parallel buses.

## Interface
- `lcd_dev.c:lcddev_register`, `lcd_dev.c:lcddev_dev_s` - Exposes an `lcd_dev_s` instance as a `/dev/lcdN` character device supporting `LCDDEVIO_*` `ioctl` operations.
- `lcd_framebuffer.c:up_fbinitialize`, `lcd_framebuffer.c:up_fbgetvplane`, `lcd_framebuffer.c:up_fbuninitialize`, `lcd_framebuffer.c:lcdfb_dev_s` - Adapts a raster `lcd_dev_s` driver into a standard NuttX framebuffer (`fb_vtable_s`) with an in-RAM shadow framebuffer.
- `lcddrv_spiif.c:lcddrv_spiif_initialize`, `skeleton.c:up_oledinitialize` - SPI LCD bus interface wrapper and reference LCD driver skeleton.
- `gc9a01.c:gc9a01_lcdinitialize`, `ili9225.c:ili9225_lcdinitialize`, `ili9340.c:ili9340_initialize`, `ili9340.c:ili9340_clear`, `ili9341.c:ili9341_initialize`, `ili9341.c:ili9341_clear`, `jd9851.c:jd9851_lcdinitialize`, `mio283qt2.c:mio283qt2_lcdinitialize`, `mio283qt9a.c:mio283qt9a_lcdinitialize`, `ra8875.c:ra8875_lcdinitialize`, `ssd1289.c:ssd1289_lcdinitialize`, `st7735.c:st7735_lcdinitialize`, `st7789.c:st7789_lcdinitialize`, `st7796.c:st7796_fbinitialize` - Initializes color TFT LCD controllers.
- `p14201.c:rit_initialize`, `pcd8544.c:pcd8544_initialize`, `ssd1306_base.c:ssd1306_initialize`, `ssd1306_base.c:ssd1306_fill`, `ssd1351.c:ssd1351_initialize`, `ssd1680.c:ssd1680_initialize`, `st7565.c:st7565_initialize`, `st7567.c:st7567_initialize`, `lpm013m091a.c:lpm013m091a_initialize`, `memlcd.c:memlcd_initialize`, `ug-2864ambag01.c:ug2864ambag01_initialize`, `ug-9664hswag01.c:ug_initialize` - Initializes monochrome/color OLED, e-paper (SSD1680), Sharp Memory LCD, and passive matrix LCD controllers.
- `apa102_lcd.c:apa102_initialize`, `max7219_lcd.c:max7219_initialize`, `ht16k33_14seg.c:ht16k33_register`, `pcf8574_lcd_backpack.c:pcf8574_lcd_backpack_register`, `st7032.c:st7032_register` - Initializes LED matrix and alphanumeric/segment display drivers.
- `ft80x.c:ft80x_register`, `ft80x_spi.c:ft80x_host_command`, `tda19988.c:tda19988_register`, `tda19988.c:tda19988_videomode`, `tda19988.c:tda19988_read_edid` - Registers FTDI FT80x EVE GPU display controllers and NXP TDA19988 HDMI transmitter drivers.

## Invariants
- `lcd_dev_s` plane methods (`getvideoinfo`, `getplaneinfo`, `putrun`, `getrun`) assert `dev != NULL`, `vinfo != NULL`, `pinfo != NULL`, `planeno == 0`, and non-null aligned pixel `buffer` pointers (e.g., `ssd1289.c:ssd1289_lcdinitialize`, `ssd1306_base.c:ssd1306_initialize`, `ssd1351.c:ssd1351_initialize`, `st7789.c:st7789_lcdinitialize`).
- Controller initialization functions assert valid underlying bus handles (`spi != NULL`, `i2c != NULL`, or `lcd != NULL`) and valid device numbers (`devno < CONFIG_SSD1306_NUMDEVS` or `devno == 0`).

## Side Effects
- Executes SPI (`SPI_LOCK`, `SPI_SELECT`, `SPI_CMDDATA`, `SPI_SEND`, `SPI_SNDBLOCK`), I2C (`I2C_TRANSFER`), and parallel bus transactions to configure panel registers and transfer pixel runs (`ssd1306_spi.c:ssd1306_sendblk`, `ssd1306_i2c.c:ssd1306_sendblk`, `st7789.c:st7789_lcdinitialize`, `st7796.c:st7796_fbinitialize`).
- Registers character devices under `/dev` via `register_driver` and acquires device mutexes via `nxmutex_lock` (`lcd_dev.c:lcddev_register`, `ft80x.c:ft80x_register`, `ht16k33_14seg.c:ht16k33_register`, `pcf8574_lcd_backpack.c:pcf8574_lcd_backpack_register`, `st7032.c:st7032_register`, `tda19988.c:tda19988_register`).
- Allocates framebuffers and device state on the kernel heap via `kmm_zalloc` and `kmm_malloc` (`lcd_framebuffer.c:up_fbinitialize`, `st7796.c:st7796_fbinitialize`, `lcd_dev.c:lcddev_register`).

## Verification
- Run: `make test`
