# 从视频中提取音频

此处整理，从视频文件中提取音频相关内容。

## 从mp4中提取音频mp3

### 提取整个音频

```bash
ffmpeg -i show_14322648_video.mp4 -b:a 128k show_14322648_audio.mp3
```

### 提取音频片段

```bash
ffmpeg -i show_157712932_video.mp4 -ss 00:00:11.270 -to 00:00:14.550 -b:a 128k show_157712932_audio_000011270_000014550.mp3
```
* 参数解释
  ```bash
  usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

  -ss time_off        set the start time offset
  -to time_stop       record or transcode stop time

  -ab bitrate         audio bitrate (please use -b:a)
  ```
