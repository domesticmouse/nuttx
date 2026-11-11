# `spresense/include` Component (`boards/arm/cxd56xx/spresense/include`)

## Overview
Board-level public headers (`include`) for `spresense` (`arm/cxd56xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 41 header file(s).

## Interface
- `[board.h:cxd56_boardinitialize]` Public declaration `cxd56_boardinitialize()`
- `[board.h:board_power_device]` Type definition `board_power_device`
- `[board.h:BOARD_FCLKOUT_FREQUENCY]` Hardware/board configuration macros (`BOARD_FCLKOUT_FREQUENCY`, `BOARD_UART0_BASEFREQ`, `BOARD_UART1_BASEFREQ`, `BOARD_UART2_BASEFREQ`, `GPIO_LED1`, `GPIO_LED2` (+64 more))
- `[board_lcdpins.h:ILI934X_RST_PIN]` Hardware/board configuration macros (`ILI934X_RST_PIN`, `ILI934X_DC_PIN`)
- `[board_pinconfig.h:PINCONF_UART2_TXD]` Hardware/board configuration macros (`PINCONF_UART2_TXD`, `PINCONF_UART2_RXD`, `PINCONF_UART2_CTS`, `PINCONF_UART2_RTS`, `PINCONF_SPI4_CS_X`, `PINCONF_SPI4_SCK` (+20 more))
- `[cxd56_ak09912.h:board_ak09912_initialize]` Public declaration `board_ak09912_initialize()`
- `[cxd56_ak09912.h:ak09912_init]` Public declaration `ak09912_init()`
- `[cxd56_ak09912.h:ak09912_scu_register]` Public declaration `ak09912_scu_register()`
- `[cxd56_alt1250.h:board_alt1250_initialize]` Public declaration `board_alt1250_initialize()`
- `[cxd56_alt1250.h:board_alt1250_uninitialize]` Public declaration `board_alt1250_uninitialize()`
- `[cxd56_alt1250.h:board_alt1250_poweron]` Public declaration `board_alt1250_poweron()`
- `[cxd56_alt1250.h:board_alt1250_poweroff]` Public declaration `board_alt1250_poweroff()`
- `[cxd56_alt1250.h:board_alt1250_powerstatus]` Public declaration `board_alt1250_powerstatus()`
- `[cxd56_alt1250.h:board_alt1250_powerkeep]` Public declaration `board_alt1250_powerkeep()`
- `[cxd56_alt1250.h:board_alt1250_reset]` Public declaration `board_alt1250_reset()`
- `[cxd56_apds9930.h:board_apds9930_initialize]` Public declaration `board_apds9930_initialize()`
- `[cxd56_apds9960.h:board_apds9960_initialize]` Public declaration `board_apds9960_initialize()`
- `[cxd56_audio.h:board_audio_power_control]` Public declaration `board_audio_power_control()`
- `[cxd56_audio.h:board_aca_power_control]` Public declaration `board_aca_power_control()`
- `[cxd56_audio.h:board_aca_power_monitor]` Public declaration `board_aca_power_monitor()`
- `[cxd56_audio.h:board_external_amp_mute_control]` Public declaration `board_external_amp_mute_control()`
- `[cxd56_audio.h:board_external_amp_mute_monitor]` Public declaration `board_external_amp_mute_monitor()`
- `[cxd56_audio.h:board_audio_i2s_enable]` Public declaration `board_audio_i2s_enable()`
- `[cxd56_audio.h:board_audio_i2s_disable]` Public declaration `board_audio_i2s_disable()`
- `[cxd56_audio.h:board_audio_initialize]` Public declaration `board_audio_initialize()`
- *(+105 additional symbols across 41 files)*

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh spresense:nsh && make`
