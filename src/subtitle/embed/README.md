# 嵌入字幕

用ffmpeg去`嵌入字幕`=`写入字幕`=`合并字幕`=`烧录字幕`

分2类：

## 软字幕=内挂字幕

* 别称：`软字幕`=`soft subs`=`soft subtitles`
* ffmpeg处理逻辑：`stream copy`**流拷贝**模式
* 举例：
    ```bash
    ffmpeg -i input.mkv -i subtitles.ass -codec copy -map 0 -map 1 output.mkv

    ffmpeg -i infile.mp4 -f srt -i infile.srt -c:v copy -c:a copy -c:s mov_text outfile.mp4
    ```

## 硬字幕=内嵌字幕

* 别称：`硬字幕`=`hardsubs`=`hard subs`=`hard subtitles`=`burn in subtitles`
* ffmpeg处理逻辑：用`-vf`加上**字幕文件**
* 前提：ffmpeg支持ass
  * 即：ffmpeg编译参数中包含：`--enable-libass`
    * 举例
        ```bash
        # ffmpeg -version
        ffmpeg version 4.2-tessus  https://evermeet.cx/ffmpeg/  Copyright (c) 2000-2019 the FFmpeg developers
        built with Apple LLVM version 10.0.1 (clang-1001.0.46.4)
        configuration: --cc=/usr/bin/clang --prefix=/opt/ffmpeg ... --enable-libass  ...
        ```
* 举例
  1. 嵌入srt字幕
    ```bash
    ffmpeg -i input.mp4 -vf "subtitles=subtitle.srt" output.mp4
    ```
    * 注
      * (1)-vf后面参数，可以不加双引号：
        ```bash
        ffmpeg -i input.mp4 -vf subtitles=subtitle.srt output.mp4
        ```
        * 不过为了区别后续其他参数，最好像上面一样加上双引号，比较容易和其他参数区别开
      * (2)如果srt字幕内在在视频文件中
        * 比如视频是mkv的容器，内挂有srt字幕，则可以：
            ```bash
            ffmpeg -i input.mkv -vf subtitles=input.mkv output.mp4
            ```
  2. 嵌入ass字幕
    ```bash
    ffmpeg -i input.mp4 -vf "ass=subtitle.ass" output.mp4
    ```
    * 举例
      ```bash
      ffmpeg -i CTT_Folge_01_CH_Subs_DefaultZhcnButNotShow.mp4 -vf ass=subtitle_fontLarggerBackgroundAlpha-4.ass fontPingFangSC20HalfTransparent.mp4
      ```
    * 特殊
      * 另外ffmpeg也支持：`Picture-based subtitles`=基于图片的字幕
        * 命令举例：
            ```bash
            ffmpeg -i input.mkv -filter_complex "[0:v][0:s]overlay[v]" -map "[v]" -map 0:a <output options> output.mkv
            ```
        * 参数说明：
          * 如果是多个stream流，可以把`[0:s]`换成对应的`[0:s:0]`或`[0:s:1]`
    * 注意：
      * （1）当视频有多个音频流，此种方式可能会破坏编码，则用下面方式去修复：
        ```bash
        ffmpeg -i input.ts -filter_complex "[0:v][0:s]overlay[v]" -map "[v]" -map 0:a:0 <output options> output.mkv
        ```
      * （2）Windows环境：注意设置字体的路径
