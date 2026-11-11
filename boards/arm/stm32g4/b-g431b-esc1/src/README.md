# `b-g431b-esc1/src` Component (`boards/arm/stm32g4/b-g431b-esc1/src`)

## Overview
Board-level C implementation (`src`) for `b-g431b-esc1` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[b-g431b-esc1.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[b-g431b-esc1.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[b-g431b-esc1.h:stm32_foc_setup]` Public declaration `stm32_foc_setup()`
- `[b-g431b-esc1.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[b-g431b-esc1.h:stm32_cansock_setup]` Public declaration `stm32_cansock_setup()`
- `[b-g431b-esc1.h:STM32_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`STM32_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS` (+7 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_cansock.c:stm32_cansock_setup]` Public function `stm32_cansock_setup()`
- `[stm32_foc.c:stm32_foc_setup]` Public function `stm32_foc_setup()`
- `[stm32_foc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_STM32_FDCAN`, `CONFIG_STM32_FDCAN_CHARDRIVER`, `CONFIG_STM32_FDCAN_SOCKET` (+1 more)
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:#error]` Compile-time guard: `No CAN is enable. Please enable at least one CAN device`
- `[stm32_cansock.c:#error]` Compile-time guard: `No CAN is enable. Please enable at least one CAN device`
- `[stm32_foc.c:DEBUGASSERT]` Requires `dev`
- `[stm32_foc.c:#error]` Compile-time guard: `Only 2-shunts configuration is supported`
- `[stm32_foc.c:#error]` Compile-time guard: `#endif`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_hall3ph_initialize()`, `board_qencoder_initialize()`, `btn_lower_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_cansock.c:stm32_cansock_setup]` Configures or drives hardware GPIO pins
- `[stm32_foc.c:stm32_foc_setup]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_foc.c:stm32_foc_setup]` Configures or drives hardware GPIO pins
- `[stm32_foc.c:stm32_foc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `foc_register()`, `stm32_foc_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh b-g431b-esc1:nsh && make`
