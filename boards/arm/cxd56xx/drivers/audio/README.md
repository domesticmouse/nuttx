# `drivers/audio` Component (`boards/arm/cxd56xx/drivers/audio`)

## Overview
Board support component `audio` for `drivers` (`arm/cxd56xx`), containing 29 source/script file(s) (`cxd56_audio.c, cxd56_audio_ac_reg.c, cxd56_audio_ac_reg.h, cxd56_audio_aca.c`).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[Kconfig:CXD56_AUDIO]` Kconfig symbols (`CONFIG_CXD56_AUDIO`)
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_checkid]` Public declaration `cxd56_audio_ac_reg_checkid()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_resetdsp]` Public declaration `cxd56_audio_ac_reg_resetdsp()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_initdsp]` Public declaration `cxd56_audio_ac_reg_initdsp()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_poweron_sdes]` Public declaration `cxd56_audio_ac_reg_poweron_sdes()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_set_micmode]` Public declaration `cxd56_audio_ac_reg_set_micmode()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_poweron_codec]` Public declaration `cxd56_audio_ac_reg_poweron_codec()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_poweroff_codec]` Public declaration `cxd56_audio_ac_reg_poweroff_codec()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_enable_serialif]` Public declaration `cxd56_audio_ac_reg_enable_serialif()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_init_selector]` Public declaration `cxd56_audio_ac_reg_init_selector()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_set_alcspc]` Public declaration `cxd56_audio_ac_reg_set_alcspc()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_poweron_dnc]` Public declaration `cxd56_audio_ac_reg_poweron_dnc()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_poweroff_dnc]` Public declaration `cxd56_audio_ac_reg_poweroff_dnc()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_disable_dnc]` Public declaration `cxd56_audio_ac_reg_disable_dnc()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_enable_dnc]` Public declaration `cxd56_audio_ac_reg_enable_dnc()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_mute_dnc]` Public declaration `cxd56_audio_ac_reg_mute_dnc()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_unmute_dnc]` Public declaration `cxd56_audio_ac_reg_unmute_dnc()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_set_dncram]` Public declaration `cxd56_audio_ac_reg_set_dncram()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_enable_deq]` Public declaration `cxd56_audio_ac_reg_enable_deq()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_disable_deq]` Public declaration `cxd56_audio_ac_reg_disable_deq()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_set_deq_param]` Public declaration `cxd56_audio_ac_reg_set_deq_param()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_poweron_cic]` Public declaration `cxd56_audio_ac_reg_poweron_cic()`
- `[cxd56_audio_ac_reg.h:cxd56_audio_ac_reg_poweroff_cic]` Public declaration `cxd56_audio_ac_reg_poweroff_cic()`
- *(+405 additional symbols across 29 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_CXD56_AUDIO`

## Side Effects
- `[cxd56_audio.c:cxd56_audio_poweron]` Initializes/registers kernel devices or filesystems (`board_audio_initialize()`)
- `[cxd56_audio_irq.c:cxd56_audio_irq_attach]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
