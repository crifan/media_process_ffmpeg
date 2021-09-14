# 用到ffmpeg的

此处整理，内部用到了ffmpeg的一些相关内容：

* `pydub`：Python的音频处理库
  * jiaaro/pydub: Manipulate audio with a simple and easy high level interface
    * https://github.com/jiaaro/pydub
      * 底层是用ffmpeg去实现音视频的处理的
* `audioread`：Python的音频解析库
  * beetbox/audioread: cross-library (GStreamer + Core Audio + MAD + FFmpeg) audio decoding for Python
    * https://github.com/beetbox/audioread
      * 底层是通过ffmpeg去解析出音频信息
* `Gifski`
  * GitHub
    * sindresorhus/Gifski: 🌈 Convert videos to high-quality GIFs on your Mac
      * https://github.com/sindresorhus/Gifski
  * 举例
    * 把多张PNG图片，转换成gif动图：
        ```bash
        TMPFILE="$(mktemp /tmp/XXXXXXXXXXX).mov"; \
            ffmpeg -f image2 -framerate 30 -i image_%06d.png -c:v prores_ks -profile:v 5 "$TMPFILE" \
            && open -a Gifski "$TMPFILE"
        ```
