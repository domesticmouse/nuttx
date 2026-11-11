# LCD Driver Interfaces (`include/nuttx/lcd`)

## Overview
Defines upper-half, lower-half, and controller-specific Liquid Crystal Display (LCD), OLED, e-paper, segment LCD (SLCD), and video bridge interfaces for NuttX. Includes the generic character/framebuffer LCD vtable (`struct lcd_dev_s`), character device ioctl bindings (`lcd_dev.h`), SPI command/data interface wrappers (`lcddrv_spiif.h`), segment LCD stream codecs (`slcd_codec.h`), and hardware driver headers for controllers such as FT80x, ILI9225/9325/9340/9341/9488, SSD1289/1306/1351/1680, ST7032/7565/7567/7735/7789/7796, RA8875, PCD8544, MAX7219, HT16K33, and TDA19988.

## Interface
- `lcd.h:struct lcd_dev_s`, `lcd.h:struct lcd_planeinfo_s`, `lcd.h:struct lcddev_area_align_s`, `lcd.h:LCD_FULL_OFF`, `lcd.h:LCD_FULL_ON`
- `lcd_dev.h:lcddev_register`, `lcd_dev.h:struct lcddev_run_s`, `lcd_dev.h:struct lcddev_area_s`, `lcd_dev.h:LCDDEVIO_PUTRUN`, `lcd_dev.h:LCDDEVIO_PUTAREA`, `lcd_dev.h:LCDDEVIO_GETPLANEINFO`, `lcd_dev.h:LCDDEVIO_GETVIDEOINFO`
- `lcd_ioctl.h:FT80X_NIOCTL_BASE`, `lcd_ioctl.h:TDA19988_NIOCTL_BASE`
- `lcddrv_spiif.h:struct lcddrv_lcd_s`, `lcddrv_spiif.h:lcddrv_spiif_initialize`, `lcddrv_spiif.h:spiif_backlight`
- `slcd_codec.h:enum slcdcode_e`, `slcd_codec.h:enum slcdret_e`, `slcd_codec.h:struct slcdstate_s`, `slcd_codec.h:slcd_encode`, `slcd_codec.h:slcd_decode`, `slcd_codec.h:slcd_put`
- `slcd_ioctl.h:struct slcd_attributes_s`, `slcd_ioctl.h:struct slcd_curpos_s`, `slcd_ioctl.h:SLCDIOC_GETATTRIBUTES`, `slcd_ioctl.h:SLCDIOC_CURPOS`
- `ft80x.h:ft80x_register`, `ft80x.h:struct ft80x_notify_s`, `ft80x.h:struct ft80x_register_s`, `ft80x.h:FT80X_IOC_CREATEDL`, `ft80x.h:FT80X_IOC_APPENDDL`
- `ili9225.h:ili9225_lcdinitialize`, `ili9325.h:ILI9325_DEVICE_CODE`, `ili9340.h:struct ili9340_lcd_s`, `ili9340.h:ili9340_initialize`, `ili9341.h:struct ili9341_lcd_s`, `ili9341.h:ili9341_initialize`, `ili9488.h:ILI9488_DEVICE_CODE`
- `ssd1289.h:ssd1289_lcdinitialize`, `ssd1306.h:ssd1306_initialize`, `ssd1306.h:ssd1306_fill`, `ssd1351.h:ssd1351_initialize`, `ssd1680.h:ssd1680_initialize`
- `st7032.h:st7032_register`, `st7565.h:st7565_initialize`, `st7567.h:st7567_initialize`, `st7735.h:st7735_lcdinitialize`, `st7789.h:st7789_lcdinitialize`, `st7796.h:st7796_fbinitialize`
- `apa102.h:apa102_initialize`, `gc9a01.h:gc9a01_lcdinitialize`, `hd4478ou.h:up_lcd1602_initialize`, `ht16k33.h:ht16k33_register`, `jd9851.h:jd9851_lcdinitialize`, `lpm013m091a.h:lpm013m091a_initialize`, `max7219.h:max7219_initialize`, `memlcd.h:memlcd_initialize`, `mio283qt2.h:mio283qt2_lcdinitialize`, `mio283qt9a.h:mio283qt9a_lcdinitialize`, `p14201.h:rit_initialize`, `pcd8544.h:pcd8544_initialize`, `pcf8574_lcd_backpack.h:pcf8574_lcd_backpack_register`, `ra8875.h:ra8875_lcdinitialize`, `tda19988.h:tda19988_register`, `ug-2864ambag01.h:ug2864ambag01_initialize`, `ug-9664hswag01.h:ug_initialize`

## Invariants
- Area and run transfer buffers passed to `lcd.h:struct lcd_planeinfo_s` callbacks (`putrun`, `putarea`, `getrun`, `getarea`) must satisfy the alignment constraints reported by `lcd.h:struct lcddev_area_align_s`.
- SPI-based OLED/e-paper drivers (`ssd1306.h:CONFIG_LCD_SSD1306_SPI`, `ssd1680.h:CONFIG_LCD_SSD1680`, `ug-2864ambag01.h:CONFIG_LCD_UG2864AMBAG01`) require `CONFIG_SPI_CMDDATA` to be enabled and `CONFIG_LCD_MAXCONTRAST` within `1..255`.

## Side Effects
- Invoking `lcd.h:struct lcd_planeinfo_s` or `lcd.h:struct lcd_dev_s` operations performs SPI, I2C, or parallel bus I/O to update display GRAM, power state, contrast, and backlight hardware.
- Device registration functions (`lcd_dev.h:lcddev_register`, `ft80x.h:ft80x_register`, `st7032.h:st7032_register`, `pcf8574_lcd_backpack.h:pcf8574_lcd_backpack_register`, `tda19988.h:tda19988_register`) register character devices in the VFS namespace.

## Verification
- Run: `make test`
