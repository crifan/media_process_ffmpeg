# 动图转视频

## gif转mp4

```bash
ffmpeg -f gif -i animation.gif animation.mp4
```

## 特殊：gif转出来的mp4播放不了？

有些gif转化出来的mp4不能被Mac的`QuickTime Player.app` 播放，需要添加`pixel formal`参数

```bash
ffmpeg -i input.gif -vf scale=420:-2,format=yuv420p out.mp4
```

* 说明
  * 使用 yunv420p 需要保证长宽为偶数，这里同时使用了`scale=420:-2`
    * [wiki中解释](https://trac.ffmpeg.org/wiki/Encode/H.264#Encodingfordumbplayers)： QuickTime Player 对 H.264 视频只支持 YUV 色域 4:2:0 方式的二次插值算法

## gif转其他视频格式

```bash
ffmpeg -f gif -i animation.gif animation.mpeg
ffmpeg -f gif -i animation.gif animation.webm
```
