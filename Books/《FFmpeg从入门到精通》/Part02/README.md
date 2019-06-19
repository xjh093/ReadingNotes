## 第1章 FFmpeg简介

1.FF 指的是 Fast Forward.

2.FFmpeg 历史
- 2000年，法国天才程序员 Fabrice Bellard 开发初版。
- 2004年，FB 找到接手人，就是至今还在维护 FFmpeg 的 Michael Niedermayer。
- 2011年3月，有人对 FFmpeg 项目的管理方式并不满意，创建了一个新项目：Libav。
- 2015年8月，Michael Niedermayer 主动辞去 FFmpeg 项目负责人的职务。
- 至本书完稿，FFmpeg 已经发布到 3.3 版本。
- blabla...

3.基本组成模块
AVFormat、AVCodec、AVFilter、AVDevice、AVUtil等模块库。

- AVFormat - 封装模块
- AVCodec  - 编解码模块
- AVFilter - 滤镜模块
- swscale  - 图像转换计算模块
- swresample - 音频转换计算模块

4.编解码工具 ffmpeg
- 例子：
   `./ffmpeg -i input.mp4 output.avi`

这条命令所做的工作：
- 获得输入源 input.mp4
- 转码
- 输出文件 output.avi

示例：`ffmpeg -i 1.mp4 out.avi`
```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf57.82.100
  Duration: 00:00:14.76, start: 0.000000, bitrate: 961 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 512x288, 863 kb/s, 15 fps, 15 tbr, 15360 tbn, 30 tbc (default)
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: aac (LC) (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 96 kb/s (default)
    Metadata:
      handler_name    : SoundHandler
Stream mapping:
  Stream #0:0 -> #0:0 (h264 (native) -> mpeg4 (native))
  Stream #0:1 -> #0:1 (aac (native) -> mp3 (libmp3lame))
Press [q] to stop, [?] for help
Output #0, avi, to 'out.avi':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    ISFT            : Lavf58.12.100
    Stream #0:0(und): Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 512x288, q=2-31, 200 kb/s, 15 fps, 15 tbn, 15 tbc (default)
    Metadata:
      handler_name    : VideoHandler
      encoder         : Lavc58.18.100 mpeg4
    Side data:
      cpb: bitrate max/min/avg: 0/0/200000 buffer size: 0 vbv_delay: -1
    Stream #0:1(und): Audio: mp3 (libmp3lame) (U[0][0][0] / 0x0055), 48000 Hz, stereo, fltp (default)
    Metadata:
      handler_name    : SoundHandler
      encoder         : Lavc58.18.100 libmp3lame
frame=  120 fps=0.0 q=11.3 size=     266kB time=00:00:08.11 bitrate= 268.3kbits/frame=  221 fps=0.0 q=15.0 Lsize=     799kB time=00:00:14.76 bitrate= 443.5kbits/s speed=16.7x    
video:539kB audio:231kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 3.823911%
```

