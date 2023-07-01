# FFmpeg

## convert hevc tag to hvc1
> Apple devices only support hvc1

```bash
ffmpeg -i input.mp4 -c:v copy -tag:v hvc1 -c:a copy output.mp4
```

## convert to hevc

```bash
ffmpeg -i input.mp4 -c:v libx265 -tag:v hvc1 output.mp4
```

## convert to hevc using Intel GPU

```bash
ffmpeg -hwaccel qsv -c:v h264_qsv -i input.mp4 -c:v hevc_qsv -global_quality 28 output.mp4
```

## convert to avc

```bash
ffmpeg -i input.mp4 -c:v libx264 -tag:v avc1 output.mp4
```


