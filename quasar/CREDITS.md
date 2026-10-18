# Credits and licenses

This repository is FFmpeg n9.0.2 (upstream `946fcce0`) with patches for Quasar's Apple player. Every change is a commit after `946fcce0`, and each commit message names the patch it came from. Quasar modified this code in 2026; `git log 946fcce0..` records what changed and when.

All five patches came through LePips/MPVUI `23ba5a72`. Commits `0002` native-dolby-vision, `0003` native-dolby-vision-compatibility, and `0004` hevc-diagnostic-levels contain code from [edde746/MPVKit at `b8b922ec`](https://github.com/edde746/MPVKit/tree/b8b922ec74b84ac3a496e29e226a3a3e91491045), by cxfksword and the MPVKit contributors, Alex Kim, and edde746. That repository's `LICENSE` was LGPL-3.0 at `b8b922ec` (2026-08-29). It was changed to GPL-3.0-only one day later, in `b9e88e80`, and that change does not reach the earlier revision. Nothing after `b8b922ec` may be taken from it. The full history is in quasar-mpv's `quasar/AVFOUNDATION_CREDITS.md`.

The MPVKit changes kept FFmpeg's LGPL-2.1-or-later file headers, but they were contributed to a repository licensed LGPL-3.0. Quasar takes the stricter reading: these files are distributed under LGPL-3.0, and so are the FFmpeg libraries built from this repository, whatever `configure` reports. The files are `libavcodec/videotoolbox.c`, `libavutil/hwcontext_videotoolbox.c`, `libavutil/hwcontext_videotoolbox.h`, `libavcodec/hevc/hevcdec.c`, and `configure`. The license text is `COPYING.LGPLv3`.

Quasar never builds with `--enable-gpl` or `--enable-nonfree`.
