# `stm3210e-eval/src` Component (`boards/arm/stm32f1/stm3210e-eval/src`)

## Overview
Board-level C implementation (`src`) for `stm3210e-eval` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm3210e-eval.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm3210e-eval.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm3210e-eval.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm3210e-eval.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm3210e-eval.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[stm3210e-eval.h:stm32_extcontextsave]` Public declaration `stm32_extcontextsave()`
- `[stm3210e-eval.h:stm32_extcontextrestore]` Public declaration `stm32_extcontextrestore()`
- `[stm3210e-eval.h:stm32_extmemgpios]` Public declaration `stm32_extmemgpios()`
- `[stm3210e-eval.h:stm32_selectnor]` Public declaration `stm32_selectnor()`
- `[stm3210e-eval.h:stm32_deselectnor]` Public declaration `stm32_deselectnor()`
- `[stm3210e-eval.h:stm32_selectsram]` Public declaration `stm32_selectsram()`
- `[stm3210e-eval.h:stm32_deselectsram]` Public declaration `stm32_deselectsram()`
- `[stm3210e-eval.h:stm32_selectlcd]` Public declaration `stm32_selectlcd()`
- `[stm3210e-eval.h:stm32_deselectlcd]` Public declaration `stm32_deselectlcd()`
- `[stm3210e-eval.h:stm32_ledpminitialize]` Public declaration `stm32_ledpminitialize()`
- `[stm3210e-eval.h:stm32_pmbuttons]` Public declaration `stm32_pmbuttons()`
- `[stm3210e-eval.h:stm32_djoy_initialization]` Public declaration `stm32_djoy_initialization()`
- `[stm3210e-eval.h:extmem_save_s]` Type definition `extmem_save_s`
- `[stm3210e-eval.h:HAVE_I2CTOOL]` Hardware/board configuration macros (`HAVE_I2CTOOL`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `MIN_IRQBUTTON` (+15 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- *(+40 additional symbols across 24 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_CUSTOM_PMINIT`, `CONFIG_ARCH_IDLE_CUSTOM`, `CONFIG_INPUT_DJOYSTICK` (+5 more)
- `[stm3210e-eval.h:stm32_bringup]` Validates preconditions and returns `-EVAL` on failure
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_bringup.c:#error]` Compile-time guard: `Only one MMC/SD slot`
- `[stm32_bringup.c:#error]` Compile-time guard: `Unrecognized STM32 board`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle != NULL`
- `[stm32_composite.c:#error]` Compile-time guard: `Unrecognized STM32 board`
- `[stm32_djoystick.c:DEBUGASSERT]` Requires `g_djoyhandler`
- `[stm32_extcontext.c:DEBUGASSERT]` Requires `save != NULL`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `i2c_register()`, `m25p_initialize()`, `sdio_initialize()`, `stm32_i2c_register()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`, `sdio_initialize()`)
- `[stm32_deselectlcd.c:stm32_deselectlcd]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_deselectnor.c:stm32_deselectnor]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_deselectsram.c:stm32_deselectsram]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_djoystick.c:stm32_djoy_initialization]` Configures or drives hardware GPIO pins
- `[stm32_djoystick.c:stm32_djoy_initialization]` Initializes/registers kernel devices or filesystems (`djoy_register()`)

## Verification
- Run: `./tools/configure.sh stm3210e-eval:nsh && make`
