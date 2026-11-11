# macos (`nuttx/arch/sim/src/sim/macos`)

## Overview
Hardware abstraction and architecture package for `macos` under `nuttx/arch/sim/src/sim/macos`, providing 0 header file(s) and 1 source file(s) (including `sim_host_avfoundation_backend.m`).

## Interface
- `[sim_host_avfoundation_backend.m:host_video_get_device_count]`
- `[sim_host_avfoundation_backend.m:host_video_is_available]`
- `[sim_host_avfoundation_backend.m:host_video_init]`
- `[sim_host_avfoundation_backend.m:host_video_uninit]`
- `[sim_host_avfoundation_backend.m:host_video_start_capture]`
- `[sim_host_avfoundation_backend.m:host_video_stop_capture]`
- `[sim_host_avfoundation_backend.m:host_video_dqbuf]`
- `[sim_host_avfoundation_backend.m:host_video_set_fmt]`
- `[sim_host_avfoundation_backend.m:host_video_try_fmt]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
