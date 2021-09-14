# FFmpeg安装

## Mac

## 只安装ffmpeg

```bash
brew install ffmpeg
```

如果想要加上很多其他`filter`=`功能模块`，则可以加上对应参数：

```bash
brew reinstall ffmpeg \
    --with-tools \
    --with-fdk-aac \
    --with-freetype \
    --with-fontconfig \
    --with-libass \
    --with-libvorbis \
    --with-libvpx \
    --with-opus \
    --with-x265
```

## 安装ffmpeg，和相关ffprobe，ffplay，甚至ffserver

去官网

[Download FFmpeg](https://ffmpeg.org/download.html)

https://ffmpeg.org/download.html

提到的：

[static FFmpeg binaries for macOS 64-bit](https://evermeet.cx/ffmpeg/)

去下载最新版本：

* `ffmpeg`：https://evermeet.cx/ffmpeg/ffmpeg-4.2.7z
* `ffprobe`：https://evermeet.cx/ffmpeg/ffprobe-4.2.7z
* `ffplay`：https://evermeet.cx/ffmpeg/ffplay-4.2.7z
* `ffserver`：https://evermeet.cx/ffmpeg/ffserver-3.4.2.7z

分别下载后，解压得到二进制文件，再拷贝到合适目录。

比如Mac中的：

`/usr/local/bin`

即可。

问：如何确认已安装好？

用which去确认

```bash
which ffmpeg
which ffprobe
which ffplay
which ffserver
```

去确认能找到

以及顺带去看看版本

```bash
ffmpeg -version
ffprobe -version
ffplay -version
ffserver -version
```
