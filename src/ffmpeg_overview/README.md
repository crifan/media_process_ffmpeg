# FFmpeg概览

* `FFmpeg`
  * 是什么：一个，功能极其强大的，音视频处理相关的库

## ffmpeg能用来干什么？

可以用`ffmpeg`做很多和音视频相关的处理。

绝大多数和音频视频字幕等相关的操作，ffmpeg都支持。

列举我之前遇到过的一些，供参考：

* 解析出视频的信息
  * 举例
    * 查看字幕属性信息
      * `ffmpeg -i xxx.mp4`
        * 输出字幕信息：
          * `Stream #0:2(zho): Subtitle: mov_text (tx3g / 0x67337874), 1280x108, 0 kb/s (default)`
    * 分辨率=宽x高
      * 用ffmpeg相关的ffprobe
        * `ffprobe -v error -select_streams v:0 -show_entries stream=height,width -of csv=s=x:p=0 input.mp4`
        * 输出：`1280x720`
* 视频去水印
  * `ffmpeg -i input.mp4 -vf "delogo=x=324:y=28:w=140:h=53" -c:a copy input_removedWatermarked.mp4`
* 从视频中提取音频并分割成多个音频片段
  * 前提：
    * 首先要有字幕文件：可以指定多个时间段
  * 对于每个时间段，用ffmpeg提取指定时间段的音频
    * `ffmpeg -i input.mp4 -ss 00:00:11.270 -to 00:00:14.550 -b:a 128k output_audio_000011270_000014550.mp3`
* 给视频加字幕=把字幕嵌入合并到视频中
  * srt字幕
    * 软字幕 内挂字幕
      * `ffmpeg -i video_no_subtitle.mp4 -i subtitle.srt -codec copy -map 0 video_with_soft_subtitle.mp4`
  * ass字幕
    * 硬字幕 内嵌字幕=嵌入ass字幕到视频中
      * `ffmpeg -i input_video.mp4 -vf ass=subtitle.ass input_video_with_ass_subtitle.mp4`
* 从视频中提取出字幕
  * `ffmpeg -i video_with_soft_subtitle.mp4 -map 0:s:0 extracted_subtitle.srt`
* 字幕类型转换
  * srt转换为ass
    * `ffmpeg -i subtitle.srt subtitle.ass`

另外还有：

* `ffmpeg`被其他工具调用：用于解析和操作音视频
  * Python的音频处理库：`pydub`
    * https://github.com/jiaaro/pydub
  * Python的音频解析库：`audioread`
    * https://github.com/beetbox/audioread
