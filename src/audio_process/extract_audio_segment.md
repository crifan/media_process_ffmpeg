# 提取音频片段

此处整理，从完整的音频文件中，提取其中一段，即提取音频片段。

## 从mp3中提取某个时间段的mp3

```bash
ffmpeg -i show_14322648_audio.mp3 -acodec copy -ss 00:00:03.110 -to 00:00:06.110 show_14322648_audio_000003110_000006110.mp3
```
* 参数解释
  * `-i`：input 输入文件
  * `-acodec copy`：
    * `-acodec` = `audio codec`：音频编码器
    * == `-c copy`
      * 等价于：
          ```bash
          ffmpeg -i show_14322648_audio.mp3 -c copy -ss 00:00:03.110 -to 00:00:06.110 show_14322648_audio_000003110_000006110_cCopy.mp3
          ```

### 官网文档

* [Stream-copy ffmpeg Documentation](https://www.ffmpeg.org/ffmpeg-all.html#Stream-copy)
  > **3.2 Stream copy**
  > 
  > &nbsp;&nbsp;&nbsp;&nbsp;Stream copy is a mode selected by supplying the copy parameter to the -codec option. It makes ffmpeg omit the decoding and encoding step for the specified stream, so it does only demuxing and muxing. It is useful for changing the container format or modifying container-level metadata
* [toc-Main-options](https://www.ffmpeg.org/ffmpeg-all.html#toc-Main-options)
  > **-t duration (input/output)**
  > 
  > &nbsp;&nbsp;&nbsp;&nbsp;When used as an input option (before -i), limit the duration of data read from the input file.
  When used as an output option (before an output url), stop writing the output after its duration reaches duration.
  duration must be a time duration specification, see (ffmpeg-utils)the Time duration section in the ffmpeg-utils(1) manual.
  -to and -t are mutually exclusive and -t has priority.
  > 
  > **-to position (input/output)**
  > 
  > &nbsp;&nbsp;&nbsp;&nbsp;Stop writing the output or reading the input at position. position must be a time duration specification, see (ffmpeg-utils)the Time duration section in the ffmpeg-utils(1) manual.
  > 
  > &nbsp;&nbsp;&nbsp;&nbsp;-to and -t are mutually exclusive and -t has priority.
  > 
  > **-ss position (input/output)**
  > 
  > &nbsp;&nbsp;&nbsp;&nbsp;When used as an input option (before -i), seeks in this input file to position. Note that in most formats it is not possible to seek exactly, so ffmpeg will seek to the closest seek point before position. When transcoding and -accurate_seek is enabled (the default), this extra segment between the seek point and position will be decoded and discarded. When doing stream copy or when -noaccurate_seek is used, it will be preserved.
  > 
  > &nbsp;&nbsp;&nbsp;&nbsp;When used as an output option (before an output url), decodes but discards input until the timestamps reach position.
  > 
  > &nbsp;&nbsp;&nbsp;&nbsp;position must be a time duration specification, see (ffmpeg-utils)the Time duration section in the ffmpeg-utils(1) manual.

### 输出举例

```bash
➜  splitAudio git:(master) ffmpeg -i show_14322648_audio.mp3 -c copy -ss 00:00:03.110 -to 00:00:06.110 show_14322648_audio_000003110_000006110_cCopy.mp3
ffmpeg version 4.0.2 Copyright (c) 2000-2018 the FFmpeg developers
  built with Apple LLVM version 10.0.0 (clang-1000.11.45.2)
  configuration: --prefix=/usr/local/Cellar/ffmpeg/4.0.2 --enable-shared --enable-pthreads --enable-version3 --enable-hardcoded-tables --enable-avresample --cc=clang --host-cflags= --host-ldflags= --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfontconfig --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-libxvid --enable-opencl --enable-videotoolbox --disable-lzma --enable-nonfree
  libavutil      56. 14.100 / 56. 14.100
  libavcodec     58. 18.100 / 58. 18.100
  libavformat    58. 12.100 / 58. 12.100
  libavdevice    58.  3.100 / 58.  3.100
  libavfilter     7. 16.100 /  7. 16.100
  libavresample   4.  0.  0 /  4.  0.  0
  libswscale      5.  1.100 /  5.  1.100
  libswresample   3.  1.100 /  3.  1.100
  libpostproc    55.  1.100 / 55.  1.100
Input #0, mp3, from 'show_14322648_audio.mp3':
  Metadata:
    major_brand     : isom
    minor_version   : 0
    compatible_brands: isomiso2avc1
    encoder         : Lavf58.12.100
  Duration: 00:00:48.27, start: 0.025057, bitrate: 128 kb/s
    Stream #0:0: Audio: mp3, 44100 Hz, stereo, fltp, 128 kb/s
    Metadata:
      encoder         : Lavc58.18
Output #0, mp3, to 'show_14322648_audio_000003110_000006110_cCopy.mp3':
  Metadata:
    major_brand     : isom
    minor_version   : 0
    compatible_brands: isomiso2avc1
    TSSE            : Lavf58.12.100
    Stream #0:0: Audio: mp3, 44100 Hz, stereo, fltp, 128 kb/s
    Metadata:
      encoder         : Lavc58.18
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
Press [q] to stop, [?] for help
size=      47kB time=00:00:02.97 bitrate= 129.5kbits/s speed=1.76e+03x
video:0kB audio:47kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 1.173211%
```
