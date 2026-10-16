# Remux before re-encode checklist

Goal: change container (e.g. MOV/MKV → MP4) without losing quality when codecs already fit.

1. Identify container vs codec (extension ≠ codec). Do not “fix” by renaming `.mov` / `.mkv` → `.mp4`.
2. Inspect streams (`ffprobe -hide_banner input` or MediaInfo).
3. If video is H.264 and audio is AAC → remux (`ffmpeg -c copy`).
4. If target player cannot decode HEVC even after remux → install a decoder, use VLC, or re-encode to H.264 once.
5. ProRes / exotic codecs for delivery → re-encode to H.264 (+ AAC); keep the master.
6. Archive the original; share only the remuxed or re-encoded file.
7. Prefer local browser WASM or desktop FFmpeg/VLC over upload sites for private / client footage.
