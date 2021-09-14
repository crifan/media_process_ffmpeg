# 强大的音视频处理工具：FFmpeg

* 最新版本：`v1.0`
* 更新时间：`20210914`

## 简介

介绍音视频处理工具FFmpeg有哪些强大的功能。先对ffmpeg进行概览，包括可以用来干什么，与之相关的ffprobe、ffplay、ffserver等工具；再介绍如何安装ffmpeg；如何用ffmpeg处理音频，比如从音频中提取某段音频片段；以及各种视频处理，包括视频属性的获取和调整，包括调整视频宽高尺寸大小；以及动图gif处理，包括视频转动图、动图转视频；以及水印处理，包括去除视频水印；从视频中提取完整音频和音频片段；字幕相关处理，包括字幕的背景知识，包括软字幕和硬字幕、常见字幕格式ass和srt；以及如何用Aegisub编辑字幕；从视频中提取字幕、从srt转换出ass字幕；嵌入字幕，包括用流拷贝模式嵌入软字幕、用vf模式烧录嵌入硬字幕、且可以指定字幕位置、指定字幕文字属性等；整理ffmpeg使用的心得和常见问题；以及其他有哪些工具软件用到了ffmpeg、如何用Python调用ffmpeg；最后给出附录内容，包括help语法、文档资料等。

## 源码+浏览+下载

本书的各种源码、在线浏览地址、多种格式文件下载如下：

### Gitbook源码

* [crifan/media_process_ffmpeg: 强大的音视频处理工具：FFmpeg](https://github.com/crifan/media_process_ffmpeg)

#### 如何使用此Gitbook源码去生成发布为电子书

详见：[crifan/gitbook_template: demo how to use crifan gitbook template and demo](https://github.com/crifan/gitbook_template)

### 在线浏览

* [强大的音视频处理工具：FFmpeg book.crifan.com](https://book.crifan.com/books/media_process_ffmpeg/website)
* [强大的音视频处理工具：FFmpeg crifan.github.io](https://crifan.github.io/media_process_ffmpeg/website)

### 离线下载阅读

* [强大的音视频处理工具：FFmpeg PDF](https://book.crifan.com/books/media_process_ffmpeg/pdf/media_process_ffmpeg.pdf)
* [强大的音视频处理工具：FFmpeg ePub](https://book.crifan.com/books/media_process_ffmpeg/epub/media_process_ffmpeg.epub)
* [强大的音视频处理工具：FFmpeg Mobi](https://book.crifan.com/books/media_process_ffmpeg/mobi/media_process_ffmpeg.mobi)

## 版权说明

此电子书教程的全部内容，如无特别说明，均为本人原创和整理。其中部分内容参考自网络，均已备注了出处。如有发现侵犯您版权，请通过邮箱联系我 `admin 艾特 crifan.com`，我会尽快删除。谢谢合作。

## 鸣谢

感谢我的老婆**陈雪**的包容理解和悉心照料，才使得我`crifan`有更多精力去专注技术专研和整理归纳出这些电子书和技术教程，特此鸣谢。

## 更多其他电子书

本人`crifan`还写了其他`100+`本电子书教程，感兴趣可移步至：

[crifan/crifan_ebook_readme: Crifan的电子书的使用说明](https://github.com/crifan/crifan_ebook_readme)
