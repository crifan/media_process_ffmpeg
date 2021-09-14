# Python

此处整理，用Python调用ffmpeg，实现音视频处理期间的相关内容。

## ffmpeg相关库函数

之前已把相关的，Python中调用ffmpeg去处理音视频相关的功能，封装成函数：

https://github.com/crifan/crifanLibPython/blob/master/python3/crifanLib/thirdParty/crifanFfmpeg.py

其中就有：

* `removeVideoWatermark`：去除视频水印
* `detectVideoDimension`：获取视频属性

需要的，可以直接拿去用。

## 用Python调用ffmpeg

### 用python代码调用ffmpeg去从mp4中（根据字幕信息）截图mp3音频片段

```bash
import subprocess
# extract audio segment from video
# ffmpeg -i show_157712932_video.mp4 -ss 00:00:11.270 -to 00:00:14.550 -b:a 128k show_157712932_audio_000011270_000014550.mp3
if not os.path.exists(curAudioSegmentFullpath):
  ffmpegCmd = "ffmpeg -i %s -ss %s -to %s -b:a 128k %s" % (showVideoFullpath, startTimeStr, endTimeStr, curAudioSegmentFullpath)
  subprocess.call(ffmpegCmd, shell=True)
```

## 心得：加`-nostdin`避免后台模式运行时卡死

Python代码中调用ffmpeg去处理视频，比如：

```bash
ffmpeg -i input_video.mp4 -vf "delogo=x=474:y=6:w=162:h=90" -c:a copy input_video_removedWatermark.mp4
```

然后正常运行Python时：

```bash
python3 processCourseVideo.py
```

没问题。

后台运行时：

```bash
python3 processCourseVideo.py &
```

结果会卡死。

后来发现：需要给`ffmpeg`加`-nostdin`参数：

```bash
ffmpeg -nostdin -i input_video.mp4 -vf "delogo=x=474:y=6:w=162:h=90" -c:a copy input_video_removedWatermark.mp4
```

能避免卡死。

详见：

【已解决】后台运行Python代码导致subprocess.check_call调用ffmpeg卡死
