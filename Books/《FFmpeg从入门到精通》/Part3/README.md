# 第2章 FFmpeg 工具使用基础

1.FFmpeg 常用的工具主要是:
- ffmpeg:  编解码工具
- ffprobe: 内容分析工具
- ffplay:  播放器

2.ffmpeg 常用命令
- `ffmpeg --help` : [1.txt]()

3.ffmpeg 常见的命令大概分为6个部分：
- ffmpeg信息查询部分
- 公共操作参数部分
- 文件主要操作参数部分
- 视频操作参数部分 
- 音频操作参数部分
- 字幕操作参数部分

4.`ffmpeg --help` 查看到的 help 信息是 ffmpeg 命令的基础信息

获得高级参数部分，使用命令：`ffmpeg --help long` -> [2.txt]()

获得全部的帮助信息，使用命令：`ffmpeg --help full` -> [3.txt]()

5.查看 ffmpeg 目前所支持的 license 协议：`ffmpeg -L`

6.查看 ffmpeg 的版本：`ffmpeg -version`

7.查看支持的编码器：`ffmpeg -encoders` -> [4.txt]()

8.查看支持的解码器：`ffmpeg -decoders` -> [5.txt]()

9.查看支持的滤镜：`ffmpeg -filters` -> [6.txt]()

10.查看 FLV 封装器的参数支持：`ffmpeg -h muxer=flv` -> [7.txt]()

11.查看 FLV 解封装器的参数支持：`ffmpeg -h demuxer=flv` -> [8.txt]()

12.查看 H.264(AVC) 的编码参数支持：`ffmpeg -h encoder=h264` -> [9.txt]()

13.查看 H.264(AVC) 的解码参数支持：`ffmpeg -h decoder=h264` -> [10.txt]()

14.查看 colorkey 滤镜的参数支持：`ffmpeg -h filter=colorkey` -> [11.txt]()

15.ffmpeg 的封装转换

16.


