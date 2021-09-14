# 转换字幕

## 从srt转换出ass字幕文件

```bash
ffmpeg -i subtitle.srt subtitle.ass
```

举例：

```bash
➜  ffmpeg_edit_subtitle ffmpeg -i subtitle.srt subtitle.ass
ffmpeg version 3.4.2 Copyright (c) 2000-2018 the FFmpeg developers
  built with Apple LLVM version 9.0.0 (clang-900.0.39.2)
  configuration: --prefix=/usr/local/Cellar/ffmpeg/3.4.2 --enable-shared --enable-pthreads --enable-version3 --enable-hardcoded-tables --enable-avresample --cc=clang --host-cflags= --host-ldflags= --disable-jack --enable-gpl --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-opencl --enable-videotoolbox --disable-lzma
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Input #0, srt, from 'subtitle.srt':
  Duration: N/A, bitrate: N/A
    Stream #0:0: Subtitle: subrip
Output #0, ass, to 'subtitle.ass':
  Metadata:
    encoder         : Lavf57.83.100
    Stream #0:0: Subtitle: ass (ssa)
    Metadata:
      encoder         : Lavc57.107.100 ssa
Stream mapping:
  Stream #0:0 -> #0:0 (subrip (srt) -> ass (ssa))
Press [q] to stop, [?] for help
size=      33kB time=00:26:17.56 bitrate=   0.2kbits/s speed=3.6e+05x
video:0kB audio:0kB subtitle:23kB other streams:0kB global headers:1kB muxing overhead: 42.551056%
```
