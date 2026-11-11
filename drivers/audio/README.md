# Audio Drivers (`drivers/audio`)

## Overview
Implements lower-half audio device drivers, I2S/DMA audio bridges, PWM tone generators, and codec/DSP drivers (CS4344, CS43L22, ES7210, ES8311, ES8388, VS1053, WM8776, WM8904, WM8994), along with null and fake audio test/simulation devices.

## Interface
- `audio_dma.c:audio_dma_initialize`, `audio_i2s.c:audio_i2s_initialize` - Wraps platform DMA channels (`audio_dma.c:audio_dma_s`) and I2S buses (`audio_i2s.c:audio_i2s_s`) as `audio_lowerhalf_s` audio streaming interfaces.
- `audio_null.c:audio_null_initialize`, `audio_fake.c:audio_fake_initialize` - Instantiates virtual/null and simulated audio lower-half drivers (`audio_null.c:null_dev_s`, `audio_fake.c:audio_fake_s`).
- `tone.c:tone_register` - Registers a character device (`tone.c:tone_upperhalf_s`) that drives a PWM lower half (`pwm_lowerhalf_s`) to play audio tones and melodies.
- `cs4344.c:cs4344_initialize`, `cs43l22.c:cs43l22_initialize`, `cs43l22_debug.c:cs43l22_dump_registers`, `cs43l22_debug.c:cs43l22_clock_analysis` - Initializes Cirrus Logic CS4344 and CS43L22 DAC/codec drivers (`cs4344.h:cs4344_dev_s`, `cs43l22.h:cs43l22_dev_s`).
- `es7210.c:es7210_initialize`, `es8311.c:es8311_initialize`, `es8311_debug.c:es8311_dump_registers`, `es8388.c:es8388_initialize`, `es8388_debug.c:es8388_dump_registers`, `esxxxx_common.h:es_word_length_e` - Initializes Everest Semiconductor ES7210, ES8311, and ES8388 audio codecs (`es7210.h:es7210_dev_s`, `es8311.h:es8311_dev_s`, `es8388.h:es8388_dev_s`).
- `vs1053.c:vs1053_initialize` - Initializes the VLSI VS1053 MP3/audio decoder over SPI (`vs1053.c:vs1053_struct_s`).
- `wm8776.c:wm8776_initialize`, `wm8904.c:wm8904_initialize`, `wm8904_debug.c:wm8904_dump_registers`, `wm8904_debug.c:wm8904_clock_analysis`, `wm8994.c:wm8994_initialize`, `wm8994_debug.c:wm8994_dump_registers`, `wm8994_debug.c:wm8994_clock_analysis` - Initializes Wolfson WM8776, WM8904, and WM8994 audio codecs (`wm8776.h:wm8776_dev_s`, `wm8904.h:wm8904_dev_s`, `wm8994.h:wm8994_dev_s`).

## Invariants
- Codec and bridge initializers require valid lower-level bus pointers (`i2c`, `spi`, `i2s`, or `dma_dev`) and return `NULL` if allocation or hardware verification fails (`audio_dma.c:audio_dma_initialize`, `audio_i2s.c:audio_i2s_initialize`, `wm8904.c:wm8904_initialize`).
- Audio buffer queues (`pendq`) must be accessed under critical sections or device locks (`devlock`) to preserve queue integrity across ISR/DMA callbacks and worker threads (`audio_dma.c:audio_dma_s`, `es8388.h:es8388_dev_s`, `wm8994.h:wm8994_dev_s`).
- `tone.c:tone_register` requires a valid `path` and `pwm_lowerhalf_s` instance (`tone != NULL`).

## Side Effects
- Performs I2C and SPI register transactions (`I2C_TRANSFER`, `SPI_SEND`) to configure codec PLLs, clocks, mixers, and power states (`cs43l22.c:cs43l22_initialize`, `es8311.c:es8311_initialize`, `vs1053.c:vs1053_initialize`, `wm8904.c:wm8904_initialize`, `wm8994.c:wm8994_initialize`).
- Allocates DMA channels (`DMA_GET_CHAN`), translates virtual addresses to physical addresses (`up_addrenv_va_to_pa`), and streams audio buffers over I2S/DMA (`audio_dma.c:audio_dma_initialize`, `audio_i2s.c:audio_i2s_initialize`).
- Spawns worker threads (`pthread_create`) or schedules work queue items (`work_queue`) to feed audio buffers and service codec interrupts (`cs43l22.c:cs43l22_initialize`, `es7210.c:es7210_initialize`, `vs1053.c:vs1053_initialize`, `wm8904.c:wm8904_initialize`, `wm8994.c:wm8994_initialize`).

## Verification
- Run: `make test`
