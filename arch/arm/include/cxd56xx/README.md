# cxd56xx (`nuttx/arch/arm/include/cxd56xx`)

## Overview
Hardware abstraction and architecture package for `cxd56xx` under `nuttx/arch/arm/include/cxd56xx`, providing 21 header file(s) and 0 source file(s) (including `adc.h`, `audio.h`, `backuplog.h`, `battery_ioctl.h`).

## Interface
- `[adc.h:cxd56_adcinitialize]`
- `[adc.h:ANIOC_USER]`
- `[adc.h:ANIOC_CXD56_START]`
- `[adc.h:ANIOC_CXD56_STOP]`
- `[adc.h:ANIOC_CXD56_FREQ]`
- `[adc.h:ANIOC_CXD56_FIFOSIZE]`
- `[audio.h:cxd56_audio_poweron]`
- `[audio.h:cxd56_audio_poweroff]`
- `[audio.h:cxd56_audio_en_cstereo]`
- `[audio.h:cxd56_audio_dis_cstereo]`
- `[audio.h:cxd56_audio_poweron_dnc]`
- `[audio.h:cxd56_audio_poweroff_dnc]`
- `[audio.h:cxd56_audio_en_dnc]`
- `[audio.h:cxd56_audio_dis_dnc]`
- `[audio.h:cxd56_audio_en_deq]`
- `[audio.h:cxd56_audio_dis_deq]`
- `[audio.h:cxd56_audio_en_input]`
- `[audio.h:cxd56_audio_en_output]`
- `[audio.h:cxd56_audio_dis_input]`
- `[audio.h:cxd56_audio_dis_output]`
- `[audio.h:cxd56_audio_set_spout]`
- `[audio.h:cxd56_audio_set_vol]`
- `[audio.h:cxd56_audio_mute_vol]`
- `[audio.h:cxd56_audio_unmute_vol]`
- `[audio.h:cxd56_audio_mute_vol_fade]`
- `[audio.h:cxd56_audio_unmute_vol_fade]`
- `[audio.h:cxd56_audio_set_beep_freq]`
- `[audio.h:cxd56_audio_set_beep_vol]`
- `[audio.h:cxd56_audio_play_beep]`
- `[audio.h:cxd56_audio_stop_beep]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
