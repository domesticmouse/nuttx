# NuttX Audio Subsystem (`audio`)

## Overview
NuttX audio subsystem upper-half character driver (`audio.c`), composite multi-lower-half audio device wrapper (`audio_comp.c`), and WAV/PCM stream parser and fast-forward subsampler (`pcm_decode.c`).

## Interface
- `[audio.c:audio_register]`
- `[audio_comp.c:audio_comp_initialize]`
- `[pcm_decode.c:pcm_decode_initialize]`

## Invariants
- `[audio.c:audio_close]` asserts `lower->ops->shutdown != NULL` when closing the last open reference (`upper->head == NULL`).
- `[audio.c:audio_start]` returns `-EPERM` if `upper->status->state == AUDIO_STATE_OPEN` (not yet prepared/configured).
- `[audio.c:audio_mmap]` requires `map->length` to equal either `upper->apbs[0]->nmaxbytes` (with `map->offset / nmaxbytes < upper->periods`) or `sizeof(struct audio_status_s)`, returning `-EINVAL` otherwise.
- `[audio.c:audio_register]` asserts `strncmp(devname, "/dev", 4) == 0` when `CONFIG_AUDIO_CUSTOM_DEV_PATH` is enabled and `CONFIG_AUDIO_DEV_ROOT` is not set.
- `[audio_comp.c:audio_comp_priv_s]` and `[pcm_decode.c:pcm_decode_s]` place `struct audio_lowerhalf_s export` as the first struct member so `struct audio_lowerhalf_s *` can be cast directly to the private state pointer.
- `[pcm_decode.c:pcm_validwav]` requires `WAV_HDR_CHUNKID`, `WAV_HDR_FORMAT`, `WAV_FMT_CHUNKID`, `WAV_FMT_CHUNKLEN`, `WAV_FMT_FORMAT`, and `nchannels < 256`, `align < 256`, `bpsamp < 256`; when `!CONFIG_AUDIO_EXCLUDE_FFORWARD`, `[pcm_decode.c:pcm_parsewav]` requires `bpsamp` in `{8, 16}`, `nchannels` in `{1, 2}`, and `align == nchannels * bpsamp / 8`, and `[pcm_decode.c:pcm_enqueuebuffer]` asserts `priv->samprate < 65535`.

## Side Effects
- `[audio.c:audio_register]` allocates `struct audio_upperhalf_s` via `kmm_zalloc`, creates `/dev/audio` (or `CONFIG_AUDIO_DEV_PATH`) directories via `mkdir`, hooks `dev->upper = audio_callback` and `dev->priv = upper`, and registers the character device via `register_driver`.
- `[audio.c:audio_open]` and `[audio.c:audio_close]` allocate/free `upper->status` via `kumm_zalloc`/`kumm_free` and per-file `struct audio_openpriv_s` via `kmm_zalloc`/`kmm_free`, and invoke `lower->ops->shutdown` on last close.
- `[audio.c:audio_ioctl]` and `[audio.c:audio_callback]` allocate/free/enqueue audio pipeline buffers (`apb_alloc`/`apb_free`/`lower->ops->enqueuebuffer`), mutate `upper->status` under `upper->lock` and `upper->spinlock`, notify poll waiters via `poll_notify`, and send `struct audio_msg_s` messages to user message queues via `file_mq_send`.
- `[audio_comp.c:audio_comp_initialize]` allocates `struct audio_comp_priv_s` and `struct audio_lowerhalf_s *` array via `kmm_zalloc`, overwrites each child lower-half's upper callback with `audio_comp_callback`, and calls `audio_register` if `name != NULL`.
- `[pcm_decode.c:pcm_decode_initialize]` allocates `struct pcm_decode_s` via `kmm_zalloc` and hooks `dev->upper = pcm_callback`; `[pcm_decode.c:pcm_enqueuebuffer]` parses WAV headers, calls `lower->ops->configure`, and modifies `apb->samp` in-place when subsampling (`pcm_subsample`).

## Verification
- Run: `make test`
