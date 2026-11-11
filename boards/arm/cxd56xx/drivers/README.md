# `drivers` Board Support Package (`boards/arm/cxd56xx/drivers`)

## Overview
Board Support Package (BSP) blueprint for `drivers` (`arm` / `cxd56xx`). Coordinates board initialization, headers, and tooling across `audio, sensors`.

## Subdirectories & Boundaries
- [`audio`](./audio/README.md) - Board support component `audio` for `drivers` (`arm/cxd56xx`), containing 29 source/script file(s) (`cxd56_audio.c, cxd56_audio_ac_reg.c, cxd56_audio_ac_reg.h, cxd56_audio_aca.c`). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`sensors`](./sensors/README.md) - Board support component `sensors` for `drivers` (`arm/cxd56xx`), containing 12 source/script file(s) (`ak09912_scu.c, apds9930_scu.c, bh1721fvc_scu.c, bh1745nuc_scu.c`). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
