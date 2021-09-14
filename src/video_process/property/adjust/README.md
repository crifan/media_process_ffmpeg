# 视频属性调整

## 播放速率

### 加倍速播放视频

```bash
ffmpeg -i input.mov -filter:v "setpts=0.5*PTS" output.mov
```

### 慢倍速播放视频

```bash
ffmpeg -i input.mov -filter:v "setpts=2.0*PTS" output.mov
```

## 定义帧率 16fps

```bash
ffmpeg -i input.mov -r 16 -filter:v "setpts=0.125*PTS" -an output.mov
```

## 静音视频（移除视频中的音频）

```bash
ffmpeg -i input.mov -an mute-output.mov
```

* 说明
  * `-an`就是禁止音频输出
