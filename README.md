# Local video container notes (MOV / MKV → MP4)

Reusable checklists, codec decision tables, and FFmpeg one-liners for remuxing or converting video containers on your own device (no upload). Companion material for the free in-browser tools at https://filetomp4.com.

## Contents

| Path | What it is |
| --- | --- |
| `data/remux-codec-matrix.csv` | When `-c copy` remux to MP4 is honest vs when to re-encode |
| `data/local-vs-upload.csv` | Local (browser/desktop) vs upload converter trade-offs |
| `checklists/network-tab-no-upload.md` | DevTools Network steps to verify a converter stays local |
| `checklists/remux-before-reencode.md` | Decision checklist before you re-encode |
| `snippets/ffmpeg-one-liners.md` | Copy-paste FFmpeg remux / H.264 encode commands |

## Quick use

1. Inspect streams with `ffprobe` (see `snippets/ffmpeg-one-liners.md`).
2. Prefer remux (`-c copy`) when codecs already fit MP4 — use `data/remux-codec-matrix.csv` and `checklists/remux-before-reencode.md`.
3. Re-encode to H.264 + AAC only when remux fails or the player cannot decode.
4. To verify a browser tool stays local, follow `checklists/network-tab-no-upload.md`.

Requires [FFmpeg](https://ffmpeg.org/) on your machine for the CLI snippets. The CSV/checklists are tool-agnostic.

## License

CC0-1.0 (public domain dedication) for the tables, checklists, and snippets in this repo. See `LICENSE`.
