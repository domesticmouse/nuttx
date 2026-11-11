# Audio Subsystem Headers (`include/nuttx/audio`)

## Overview
Defines the NuttX audio subsystem architecture, including upper-half character device registration, audio pipeline buffer (`ap_buffer_s`) management, lower-half codec/device operation tables, I2S bus interfaces, PCM/WAV header parsers, PWM tone generation, and codec driver initializers.

## Interface
- `audio.h:audio_ops_s`, `audio.h:audio_lowerhalf_s`, `audio.h:ap_buffer_s`, `audio.h:audio_buf_desc_s`, `audio.h:audio_caps_s`, `audio.h:audio_info_s` - Core lower-half audio device vtable, audio pipeline buffer descriptor, and capability/format structures.
- `audio.h:audio_register`, `audio.h:apb_alloc`, `audio.h:apb_free`, `audio.h:apb_reference` - Audio device VFS registration and reference-counted audio pipeline buffer allocation/deallocation.
- `audio.h:AUDIOIOC_GETCAPS`, `audio.h:AUDIOIOC_RESERVE`, `audio.h:AUDIOIOC_CONFIGURE`, `audio.h:AUDIOIOC_START`, `audio.h:AUDIOIOC_STOP`, `audio.h:AUDIOIOC_ENQUEUEBUFFER`, `audio.h:AUDIOIOC_REGISTERMQ` - Standard audio `ioctl` control commands.
- `i2s.h:i2s_dev_s`, `i2s.h:i2s_ops_s`, `i2s.h:i2s_callback_t`, `i2s.h:i2schar_register`, `i2s.h:I2S_SEND`, `i2s.h:I2S_RECEIVE` - Inter-IC Sound (I2S) bus driver vtable, dispatch macros, and character device wrapper registration.
- `audio_comp.h:audio_comp_initialize`, `audio_dma.h:audio_dma_initialize`, `audio_fake.h:audio_fake_initialize`, `audio_i2s.h:audio_i2s_initialize`, `audio_null.h:audio_null_initialize`, `pcm.h:pcm_decode_initialize`, `tone.h:tone_register` - Composite, DMA, I2S, null, fake, PCM decoder, and PWM tone audio lower-half drivers.
- `cs4344.h:cs4344_initialize`, `cs43l22.h:cs43l22_initialize`, `es7210.h:es7210_initialize`, `es8311.h:es8311_initialize`, `es8388.h:es8388_initialize`, `vs1053.h:vs1053_initialize`, `wm8776.h:wm8776_initialize`, `wm8904.h:wm8904_initialize`, `wm8994.h:wm8994_initialize` - External I2C/SPI/I2S audio codec and ADC/DAC lower-half initializers.

## Invariants
- `audio.h:CONFIG_AUDIO` must be enabled for audio subsystem headers and codec drivers; codec drivers (`cs4344.h`, `cs43l22.h`, `es8311.h`, `es8388.h`, `wm8904.h`, `wm8994.h`) additionally enforce `CONFIG_SCHED_WORKQUEUE` and `INFLIGHT <= 255` at compile time.
- `audio.h:ap_buffer_s` buffers are reference-counted via `apb_reference` and must only be released through `apb_free`.

## Side Effects
- `audio.h:audio_register`, `i2s.h:i2schar_register`, and `tone.h:tone_register` create device nodes in the VFS.
- `audio.h:apb_alloc` and `audio.h:apb_free` allocate and free heap memory for audio buffers.
- Codec and I2S initializers (`cs43l22_initialize`, `es8388_initialize`, `wm8904_initialize`, etc.) perform I2C/SPI register configuration, spawn worker threads, and schedule DMA/I2S transfers.

## Verification
- Run: `make test`
