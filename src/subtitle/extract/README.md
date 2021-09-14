# 提取字幕

从视频中提取字幕文件

* 前提
  * 原视频中有字幕（的流）= 有soft`软字幕`
    * 特殊情况：
      * 有种字幕是被合并编码成视频数据本身的情况，是没有字幕的
          * 这种视频 表面上看有字幕显示出来，但是无法提取出字幕的


## 从视频中提取srt字幕

命令：

```bash
ffmpeg -i video_file.mp4 -map 0:s:0 subtitle.srt
```

参数含义：

* `-i video_file.mp4`：
  * input输入文件是video_file.mp4
* `-map 0:s:0 subtitle.srt`的含义：
  * `-map`：高级参数
  * `0:s:0`：
    * `0` -> `input_file_id`=`文件id`，输入的文件索引编号
      * 此处就一个文件，所以`0`表示此处输入的mp4视频：video_file.mp4
    * `:s` -> `:stream_specifier`, 流stream选择的是字幕subtitle 
    * `:0` -> `:stream_specifier` 第`0`个字幕
      * 此处只有一个字幕，就是这个唯一的字幕
  * `subtitle.srt`：输出的字幕文件名
