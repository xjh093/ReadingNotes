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


