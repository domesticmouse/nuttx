# `nucleo-g491re/src` Component (`boards/arm/stm32g4/nucleo-g491re/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-g491re` (`arm/stm32g4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, user/auto LED control (`LD2`), and user button (`B1`) driver registration across 1 header and 5 source files.

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-g491re.h:stm32_bringup]` Public declaration `stm32_bringup(void)`
- `[nucleo-g491re.h:GPIO_LD2]` Hardware/board GPIO macros (`GPIO_LD2`, `GPIO_BTN_USER`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`)
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize(void)`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on(int led)`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off(int led)`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize(void)`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize(void)`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup(void)`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize(void)`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons(void)`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq(int id, xcpt_t irqhandler, void *arg)`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize(void)`
- `[stm32_userleds.c:board_userled]` Public function `board_userled(int led, bool ledon)`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all(uint32_t ledset)`

## Invariants
- `[Make.defs:CONFIG_ARCH_LEDS]` Compiles `stm32_autoleds.c` when `CONFIG_ARCH_LEDS=y`, otherwise `stm32_userleds.c`; compiles `stm32_buttons.c` when `CONFIG_ARCH_BUTTONS=y`.
- `[stm32_buttons.c:board_button_irq]` Returns `-EINVAL` if `id != BUTTON_USER`.

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` and `[stm32_userleds.c:board_userled_initialize]` Configure and drive `GPIO_LD2` (`PA5`) via `stm32_configgpio` and `stm32_gpiowrite`.
- `[stm32_buttons.c:board_button_initialize]` and `[stm32_buttons.c:board_button_irq]` Configure `GPIO_BTN_USER` (`PC13`) and attach EXTI interrupts via `stm32_gpiosetevent`.
- `[stm32_bringup.c:stm32_bringup]` Initializes common STM32 board features (`stm32_common_initialize()`) and registers `/dev/buttons` (`btn_lower_initialize("/dev/buttons")`).

## Verification
- Run: `./tools/configure.sh nucleo-g491re:nsh && make`
