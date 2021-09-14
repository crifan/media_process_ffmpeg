# 视频转动图gif

## 视频转成动图(gif)

```bash
ffmpeg -i small.mp4 small.gif
```

## 转化视频中的一部分为 GIF

从视频中第二秒开始，截取时长为3秒的片段转化为 gif

```bash
ffmpeg -t 3 -ss 00:00:02 -i small.webm small-clip.gif
```

## 转化高质量 GIF

默认转化是中等质量模式，若要转化出高质量的 gif，可以修改比特率

```bash
ffmpeg -i small.mp4 -b 2048k small.gif
```
