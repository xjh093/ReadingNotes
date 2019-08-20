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

17.













