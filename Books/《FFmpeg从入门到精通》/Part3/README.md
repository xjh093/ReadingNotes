# 第2章 FFmpeg 工具使用基础

1.FFmpeg 常用的工具主要是:
- ffmpeg:  编解码工具
- ffprobe: 内容分析工具
- ffplay:  播放器

2.ffmpeg 常用命令
- `ffmpeg --help` : [1.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/1.txt)

3.ffmpeg 常见的命令大概分为6个部分：
- ffmpeg信息查询部分
- 公共操作参数部分
- 文件主要操作参数部分
- 视频操作参数部分 
- 音频操作参数部分
- 字幕操作参数部分

4.`ffmpeg --help` 查看到的 help 信息是 ffmpeg 命令的基础信息

获得高级参数部分，使用命令：`ffmpeg --help long` -> [2.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/2.txt)

获得全部的帮助信息，使用命令：`ffmpeg --help full` -> [3.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/3.txt)

5.查看 ffmpeg 目前所支持的 license 协议：`ffmpeg -L`

6.查看 ffmpeg 的版本：`ffmpeg -version`

7.查看支持的编码器：`ffmpeg -encoders` -> [4.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/4.txt)

8.查看支持的解码器：`ffmpeg -decoders` -> [5.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/5.txt)

9.查看支持的滤镜：`ffmpeg -filters` -> [6.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/6.txt)

10.查看 FLV 封装器的参数支持：`ffmpeg -h muxer=flv` -> [7.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/7.txt)

11.查看 FLV 解封装器的参数支持：`ffmpeg -h demuxer=flv` -> [8.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/8.txt)

12.查看 H.264(AVC) 的编码参数支持：`ffmpeg -h encoder=h264` -> [9.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/9.txt)

13.查看 H.264(AVC) 的解码参数支持：`ffmpeg -h decoder=h264` -> [10.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/10.txt)

14.查看 colorkey 滤镜的参数支持：`ffmpeg -h filter=colorkey` -> [11.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/%E3%80%8AFFmpeg%E4%BB%8E%E5%85%A5%E9%97%A8%E5%88%B0%E7%B2%BE%E9%80%9A%E3%80%8B/Part3/11.txt)

15.ffmpeg 的封装转换

ffmpeg 的封装转换(转封装)功能包含在 AVFormat 模块中，通过 libavformat 库进行 Mux 和 Demux 操作。

ffmpeg AVFormatContext 主要参数帮助

- avioflags - 标记 - format的缓冲设置，默认是0，就是有缓冲
    - direct - 无缓冲状态
    
- probesize - 整数 - 在进行媒体数据处理前获得文件内容的大小，可用在预计取文件头时提高速度，也可以设置足够大的值来读取到足够多的音视频数据信息

- fflags - 标记 - 
    - flush_packets - 立即将 packets 数据刷新写入文件中
    - genpts - 输出时按照正常规则产生 pts
    - nofillin - 不填写可以精确计算缺失的值
    - igndts - 忽略 dts
    - discardcorrupt - 丢弃损坏的帧
    - sortdts - 尝试以 dts 的顺序为准输出
    - keepside - 不合并数据
    - fastseek - 快速 seek (定位)操作，但是不够精确
    - latm - 设置 RTP MP4_LATM 生效
    - nobuffer - 直接读取或写出，不存入 buffer, 用于在直播采集时降低延迟
    - bitexact - 不写入随机或不稳定的数据
- seek2any - 整数 - 支持随意位置 seek, 这个 seek 不以 keyframe 为参考
- analyzeduration - 整数 - 指定解析媒体所需要花销的时间，这里设置的值越高，解析越准确，如果在直播中为了降低延迟，这个值可以高雷得低一些
- codec_whitelist - 列表 - 设置可以解析的 codec 的白名单
- format_whitelist - 列表 - 设置可以解析的 format 的白名单
- output_ts_offset - 整数 - 设置输出文件的起始时间

16.ffmpeg 的转码参数

ffmpeg 编解码部分的功能主要是通过模块 AVCodec 来完成的，通过 libavcodec 库进行 Encode 和 Decode 操作

ffmpeg AVCodecContext 主要参数帮助

- b - 整数 - 设置音频与视频码率，可以认为是音视频加起来的码率，默认为 200kbit/s，使用这个参数可以根据 b:v 设置视频码率，b:a 设置音频码率

- ab - 整数 - 设置音频码率，默认是 128kbit/s

- g - 整数 - 设置视频 GOP (可以理解为关键帧间隔)大小，默认是 12 帧一个 GOP

- ar - 整数 - 设置音频采样率，默认为 0

- ac - 整数 - 设置音频通道数，默认为 0

- bf - 整数 - 设置连续编码为 B 帧的个数，默认为 0

- maxrate - 整数 - 最大码率设置，与 bufsize 一同使用即可，默认为 0

- minrate - 整数 - 最小码率设置，配合 maxrate 与 bufsize 可以设置为 CBR 模式，平时很少使用，默认为 0

- bufsize - 整数 - 设置控制码率的 buffer 的大小，默认为 0

- keyint_min - 整数 - 设置关键帧最小间隔，默认为 25

- sc_threshold - 整数 - 设置场景切换支持，默认为 0

- me_threshold - 整数 - 设置运动估计阈值，默认为 0

- mb_threshold - 整数 - 设置宏块阈值，默认为 0

- profile - 整数 - 设置音视频的 profile, 默认为 -99

- level - 整数 - 设置音视频的 level, 默认为 -99

- timecode_frame_start - 整数 - 设置 GOP 帧的开始时间，需要在 non-drop-frame 默认情况下使用

- channel_layout - 整数 - 设置音频通道的布局格式

- threads - 整数 - 设置编解码工作的线程数

17.ffmpeg 工具的主要用途为编码、解码、转码以及媒体格式转换，ffmpeg 常用于进行转码操作

如果转码操作涉及封装的改变，则可以通过设置 AVCodec 与 AVFormat 的操作参数进行封装与编码的改变

例子：

`ffmpeg -i ~/Movies/input1.rmvb -vcodec mpeg4 -b:v 200k -r 15 -an output.mp4`

- 转封装格式从 RMVB 格式转换为 MP4 格式
- 视频编码从 RV40 转换为 MPEG4 格式
- 视频码率从原来的 377kbit/s 转换为 200kbit/s
- 视频帧率从原来的 23.98 fps 转换为 15fps
- 转码后的文件中不包括音频(-an参数)

18.`ffprobe --help` 查看 ffprobe 的参数 -> [12.txt](https://github.com/xjh093/ReadingNotes/blob/master/Books/《FFmpeg从入门到精通》/Part3/12.txt)

19.使用 `ffprobe -show_packets input.flv` 查看多媒体数据包信息。

相关信息使用标签 PACKET 括起来

例子：
```
[PACKET]
codec_type=video
stream_index=0
pts=0
pts_time=0.000000
dts=0
dts_time=0.000000
duration=1024
duration_time=0.066667
size=35377
pos=336
flags=K_
[/PACKET]
```

packet 字段说明：

| 字段 | 含义 |
| --- | --- |
| codec_type    | 多媒体类型，如视频包，音频包等
| stream_index  | 多媒体的 stream 索引
| pts           | 多媒体的显示时间值
| pts_time      | 根据不同格式计算过后的多媒体的显示时间
| dts           | 多媒体解码时间值
| dts_time      | 根据不同格式计算过后的多媒体的解码时间
| duration      | 多媒体占用的时间值
| duration_time | 根据不同格式计算过后的多媒体包所占的时间值
| size          | 多媒体包的大小
| pos           | 多媒体包所在的文件偏移位置
| flags         | 多媒体包标志，如关键包与非关键包的标记

20.通过 `ffprobe -show_data -show_packets input.flv` 组合参数来查看包中的具体数据

21.通过 `ffprobe -show_format output.mp4` 查看多媒体的封装格式。

相关信息使用标签 FORMAT 括起来

例子：
```
[FORMAT]
filename=output.mp4
nb_streams=2
nb_programs=0
format_name=mov,mp4,m4a,3gp,3g2,mj2
format_long_name=QuickTime / MOV
start_time=0.000000
duration=14.763000
size=1774234
bit_rate=961449
probe_score=100
TAG:major_brand=isom
TAG:minor_version=512
TAG:compatible_brands=isomiso2avc1mp41
TAG:encoder=Lavf57.82.100
[/FORMAT]
```

format 字段说明：

| 字段 | 含义 |
| --- | --- |
| filename         | 文件名
| nb_streams       | 媒体中包含的流的个数
| nb_programs      | 节目数
| format_name      | 使用的封装模块的名称
| format_long_name | 封装的完整名称
| start_time       | 媒体文件的起始时间
| duration         | 媒体文件的总时间长度
| size             | 媒体文件大小
| bit_rate         | 媒体文件码率

22.通过 `ffprobe -show_frames 1.mp4` 查看视频文件中的帧信息

输出的信息使用 FRAME 标签括起来

例子:
```
[FRAME]
media_type=video
stream_index=0
key_frame=1
pkt_pts=0
pkt_pts_time=0.000000
pkt_dts=0
pkt_dts_time=0.000000
best_effort_timestamp=0
best_effort_timestamp_time=0.000000
pkt_duration=1024
pkt_duration_time=0.066667
pkt_pos=336
pkt_size=35377
width=512
height=288
pix_fmt=yuv420p
sample_aspect_ratio=N/A
pict_type=I
coded_picture_number=0
display_picture_number=0
interlaced_frame=0
top_field_first=0
repeat_pict=0
color_range=unknown
color_space=unknown
color_primaries=unknown
color_transfer=unknown
chroma_location=left
[/FRAME]
```

frame 字段说明：

| 属性 | 说明 | 值 |
| --- | --- | --- |
| media_type | 帧的类型(视频、音频、字幕等) | video |
| stream_index | 帧所在的索引区域 | 0 |
| key_frame | 是否为关键帧 | 1 |
| pkt_pts | Frame包的 pts | 0 |
| pkt_pts_time | Frame包的 pts 的时间显示  | 0.000000 |
| pkt_dts | Frame包的 dts | 0 |
| pkt_dts_time | Frame包的 dts 的时间显示 | 0.000000 |
| pkt_duration | Frame包的时长 | 1024 |
| pkt_duration_time | Frame包的时长时间显示 | 0.066667 |
| pkt_pos | Frame包所在文件的偏移位置 | 336 |
| width | 帧的显示宽度 | 512 |
| height | 帧的显示高度 | 288 |
| pix_fmt | 帧的图像色彩格式 | yuv420p |
| pict_type | 帧类型 | I |

23.















