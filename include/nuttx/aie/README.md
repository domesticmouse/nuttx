# AI Engine Subsystem Headers (`include/nuttx/aie`)

## Overview
Defines the upper-half registration API and lower-half driver operations vtable for the NuttX AI Engine (`aie`) hardware acceleration framework.

## Interface
- `ai_engine.h:aie_cmd_e` - Enumeration of AI engine control commands (`AIE_CMD_LOAD`, `AIE_CMD_FEED_INPUT`, `AIE_CMD_GET_OUTPUT`).
- `ai_engine.h:aie_ops_s` - Lower-half operation callbacks (`init`, `deinit`, `feed_input`, `get_output`, `control`).
- `ai_engine.h:aie_lowerhalf_s` - Lower-half device instance structure holding a pointer to `aie_ops_s`.
- `ai_engine.h:aie_register` - Registers an AI Engine character driver node at `path` bound to a lower-half instance.

## Invariants
- `ai_engine.h:aie_lowerhalf_s` must populate a non-null `ops` pointer (`ai_engine.h:aie_ops_s`) prior to calling `ai_engine.h:aie_register`.
- Session/context `id` returned by `aie_ops_s.init` must be passed to subsequent `feed_input`, `get_output`, `control`, and `deinit` invocations.

## Side Effects
- `ai_engine.h:aie_register` allocates upper-half driver state and registers a character device in the NuttX VFS.
- `ai_engine.h:aie_ops_s` callbacks interact with AI accelerator hardware/firmware to load models, transfer input/output tensors, and release hardware contexts.

## Verification
- Run: `make test`
