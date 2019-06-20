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

示例1：`ffmpeg -i 1.mp4 out.avi`

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

示例2：`ffmpeg -i 1.mp4 -f avi out.dat`

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
Output #0, avi, to 'out.dat':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    ISFT            : Lavf58.20.100
    Stream #0:0(und): Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 512x288, q=2-31, 200 kb/s, 15 fps, 15 tbn, 15 tbc (default)
    Metadata:
      handler_name    : VideoHandler
      encoder         : Lavc58.35.100 mpeg4
    Side data:
      cpb: bitrate max/min/avg: 0/0/200000 buffer size: 0 vbv_delay: -1
    Stream #0:1(und): Audio: mp3 (libmp3lame) (U[0][0][0] / 0x0055), 48000 Hz, stereo, fltp (default)
    Metadata:
      handler_name    : SoundHandler
      encoder         : Lavc58.35.100 libmp3lame
frame=  221 fps=0.0 q=15.0 Lsize=     799kB time=00:00:14.76 bitrate= 443.5kbits/s speed=40.6x    
video:539kB audio:231kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 3.823911%
```

参数`-f`
- 制定了输出文件的容器格式

5.ffmpeg 的主要工作流程相对比较简单
- 1.解封装(Demuxing)
- 2.解码(Decoding)
- 3.编码(Encoding)
- 4.封装(Muxing)

其中需要经过6个步骤：
- 1.读取输入源
- 2.进行音视频的解封装
- 3.解码每一帧音视频数据
- 4.编码每一帧音视频数据 
- 5.进行音视频的重新封装
- 6.输出到目标

6.FFmpeg 的播放器 ffplay
- 系统需要有SDL的基础支撑

7.FFmpeg 的多媒体分析器 ffprobe

示例1：`ffprobe -show_streams out.dat`

```
Input #0, avi, from 'out.dat':
Metadata:
encoder         : Lavf58.20.100
Duration: 00:00:14.80, start: 0.000000, bitrate: 442 kb/s
Stream #0:0: Video: mpeg4 (Simple Profile) (FMP4 / 0x34504D46), yuv420p, 512x288 [SAR 1:1 DAR 16:9], 299 kb/s, 15 fps, 15 tbr, 15 tbn, 15 tbc
Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, stereo, fltp, 128 kb/s
[STREAM]
index=0
codec_name=mpeg4
codec_long_name=MPEG-4 part 2
profile=Simple Profile
codec_type=video
codec_time_base=1/15
codec_tag_string=FMP4
codec_tag=0x34504d46
width=512
height=288
coded_width=512
coded_height=288
has_b_frames=0
sample_aspect_ratio=1:1
display_aspect_ratio=16:9
pix_fmt=yuv420p
level=1
color_range=unknown
color_space=unknown
color_transfer=unknown
color_primaries=unknown
chroma_location=left
field_order=unknown
timecode=N/A
refs=1
quarter_sample=false
divx_packed=false
id=N/A
r_frame_rate=15/1
avg_frame_rate=15/1
time_base=1/15
start_pts=0
start_time=0.000000
duration_ts=222
duration=14.800000
bit_rate=299512
max_bit_rate=N/A
bits_per_raw_sample=N/A
nb_frames=222
nb_read_frames=N/A
nb_read_packets=N/A
DISPOSITION:default=0
DISPOSITION:dub=0
DISPOSITION:original=0
DISPOSITION:comment=0
DISPOSITION:lyrics=0
DISPOSITION:karaoke=0
DISPOSITION:forced=0
DISPOSITION:hearing_impaired=0
DISPOSITION:visual_impaired=0
DISPOSITION:clean_effects=0
DISPOSITION:attached_pic=0
DISPOSITION:timed_thumbnails=0
[/STREAM]
[STREAM]
index=1
codec_name=mp3
codec_long_name=MP3 (MPEG audio layer 3)
profile=unknown
codec_type=audio
codec_time_base=1/48000
codec_tag_string=U[0][0][0]
codec_tag=0x0055
sample_fmt=fltp
sample_rate=48000
channels=2
channel_layout=stereo
bits_per_sample=0
id=N/A
r_frame_rate=0/0
avg_frame_rate=0/0
time_base=3/125
start_pts=0
start_time=0.000000
duration_ts=616
duration=14.784000
bit_rate=128208
max_bit_rate=N/A
bits_per_raw_sample=N/A
nb_frames=616
nb_read_frames=N/A
nb_read_packets=N/A
DISPOSITION:default=0
DISPOSITION:dub=0
DISPOSITION:original=0
DISPOSITION:comment=0
DISPOSITION:lyrics=0
DISPOSITION:karaoke=0
DISPOSITION:forced=0
DISPOSITION:hearing_impaired=0
DISPOSITION:visual_impaired=0
DISPOSITION:clean_effects=0
DISPOSITION:attached_pic=0
DISPOSITION:timed_thumbnails=0
[/STREAM]
```

8.查看支持的编解码器
`ffmpeg -codecs`

示例：

9.查看支持的封装格式
`ffmpeg -formats`

示例：

10.查看支持的滤镜
`ffmpeg -filters`

示例：

