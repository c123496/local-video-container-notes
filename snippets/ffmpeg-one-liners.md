# FFmpeg one-liners (MOV / MKV → MP4)

## Remux (stream copy, no re-encode)

```bash
ffmpeg -i input.mov -c copy -movflags +faststart output.mp4
ffmpeg -i input.mkv -c copy -movflags +faststart output.mp4
```

Map only first video + first audio if extra tracks confuse the muxer:

```bash
ffmpeg -i input.mov -map 0:v:0 -map 0:a:0? -c copy -movflags +faststart output.mp4
```

## Compatibility encode (H.264 + AAC)

```bash
ffmpeg -i input.mkv -c:v libx264 -crf 23 -preset medium -c:a aac -b:a 128k -movflags +faststart output.mp4
```

## Inspect first

```bash
ffprobe -hide_banner input.mov
ffprobe -hide_banner input.mkv
```

If FFmpeg errors with “could not find tag” / incompatible codec for `-c copy`, re-encode that track instead of forcing a broken remux.
