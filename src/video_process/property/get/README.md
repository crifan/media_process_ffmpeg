# 获取视频属性

## 用ffprobe获取视频分辨率 宽度和高度

```bash
ffprobe -v error -select_streams v:0 -show_entries stream=width,height -of csv=s=x:p=0 video_file.mp4
```

举例：

```bash
# ffprobe -v error -select_streams v:0 -show_entries stream=width,height -of csv=s=x:p=0 course_1608_video_normalWatermark_477w360h.mp4
480x360
```

## 查看视频基本信息

通过：

```bash
ffmpeg -i xxx.mp4
```

即可看到mp4视频的信息，其中包括了字幕的信息：

```bash
    Stream #0:2(zho): Subtitle: mov_text (tx3g / 0x67337874), 1280x108, 0 kb/s (default)
    Metadata:
      creation_time   : 2018-10-13T03:27:31.000000Z
      handler_name    : SubtitleHandler
```

其中：

* `Stream #0:2`：字幕也是一个stream流，index是0:2
* `zho`：(应该)表示是中文
* `mov_text`：后来才听说，好像指的是`Apple Mov Text`格式的？

### 举例1

```bash
➜  ffmpeg_edit_subtitle ffmpeg -i CTT_Folge_01_CH_Subs_DefaultZhcnButNotShow.mp4
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
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'CTT_Folge_01_CH_Subs_DefaultZhcnButNotShow.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    creation_time   : 2018-10-13T03:27:31.000000Z
    encoder         : HandBrake 1.1.2 2018090500
  Duration: 00:26:52.03, start: -0.001333, bitrate: 1762 kb/s
    Stream #0:0(und): Video: h264 (Main) (avc1 / 0x31637661), yuv420p(tv, bt709), 1280x720 [SAR 1:1 DAR 16:9], 1599 kb/s, 25 fps, 25 tbr, 90k tbn, 180k tbc (default)
    Metadata:
      creation_time   : 2018-10-13T03:27:31.000000Z
      handler_name    : VideoHandler
    Stream #0:1(eng): Audio: aac (LC) (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 157 kb/s (default)
    Metadata:
      creation_time   : 2018-10-13T03:27:31.000000Z
      handler_name    : Stereo
    Stream #0:2(zho): Subtitle: mov_text (tx3g / 0x67337874), 1280x108, 0 kb/s (default)
    Metadata:
      creation_time   : 2018-10-13T03:27:31.000000Z
      handler_name    : SubtitleHandler
At least one output file must be specified
```

看到字幕了：`Stream #0:2(zho)`

zho应该是中文

且显示已经是default了，即默认是中文字幕（而不是之前的英文字幕）

### 举例2

```bash
ffmpeg -i 1xx-我来保证你们的安全.mp4
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
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1xxx-我来保证你们的安全.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 0
    compatible_brands: isomiso2avc1
    creation_time   : 2018-01-28T05:46:37.000000Z
  Duration: 00:01:26.24, start: 0.000000, bitrate: 606 kb/s
    Stream #0:0(eng): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 640x360 [SAR 1:1 DAR 16:9], 541 kb/s, 25 fps, 25 tbr, 12800 tbn, 50 tbc (default)
    Stream #0:1(eng): Audio: aac (LC) (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 62 kb/s (default)
    Metadata:
      creation_time   : 2018-01-28T05:46:35.000000Z
At least one output file must be specified
```

中并没有`Subtitle`的信息

-> 看来这个视频本身就不包含独立的字幕

-> 没法用ffmpeg去提取字幕了
