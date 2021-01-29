## FFmpeg 视频处理



支持视频编码格式  H.262 H.264 H.265 VP8 VP9 AV1

支持音频编码格式  MP3 ACC



### 查看 FFmpeg 支持的容器 MP4 MKV WebM AVI

`ffmpeg -formats `



### 查看 FFmpeg 支持的编码格式

`ffmpeg -codecs`



### 查看视频文件的元信息

`ffmpeg -i input.mp4 -hide_banner`





### 使用格式

ffmpeg [全局参数] [输入文件参数] -i 输入文件 输出文件参数 输出文件



### FFmpeg 常用的命令行参数

​		-c：指定编码器

​		-c copy：直接复制，不经过重新编码（这样比较快）

​		-c:v：指定视频编码器

​		-c:a：指定音频编码器

​		-i：指定输入文件

​		-an：去除音频流

​		-vn： 去除视频流

​		-preset：指定输出的视频质量，会影响文件的生成速度，有以下几个可用的值 ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow。

​		-y：不经过确认，输出时直接覆盖同名文件。





### 转换编码格式

`ffmpeg -i input.mp4  -c:v libx264 output.mp4`



### 转换容器格式

`ffmpeg -i input.mp4 -c copy output.webm`



### 调整码率 改变编码的比特率，下面的例子指定码率最小为964K，最大为3856K，缓冲区大小为 2000K

`ffmpeg -i input.mp4 -minrate 964K -maxrate 3856K -bufsize 2000K output.mp4`



### 改变分辨率

`ffmpeg -i input.mp4 -vf scale=480:-1 output.mp4`



### 提取音频 -vn表示去掉视频，-c:a copy表示不改变音频编码，直接拷贝

`ffmpeg -i input.mp4 -vn -c:a copy output.aac`



### 添加音轨

`ffmpeg -i input.aac -i input.mp4 output.mp4`



### 从指定时间开始，连续对1秒钟的视频进行截图 %3d 指明使用3位数字来补充完整文件名

`ffmpeg -i input.mp4 -ss 00:01:24 -t 00:00:01 output_%3d.jpg`



### 截一张图 -vframes 1指定只截取一帧，-q:v 2表示输出的图片质量，一般是1到5之间（1 为质量最高）

`ffmpeg -ss 01:23:45 -i input -vframes 1 -q:v 2 output.jpg`



### 裁剪视频片段 -c copy表示不改变音频和视频的编码格式，直接拷贝，这样会快很多

`ffmpeg -ss 00:01:50 -i input.mp4 -t 10.5 -c copy output.mp4`

`ffmpeg -ss 2.5 -i input.mp4 -to 10 -c copy output.mp4`



### 将音频文件，转为带封面的视频文件 -loop 1参数表示图片无限循环，-shortest参数表示音频文件结束，输出视频就结束

`ffmpeg -loop 1 -i cover.jpg -i input.mp3 -c:v libx264 -c:a aac -b:a 192k -shortest output.mp4`



参考文档： https://www.bookstack.cn/read/other-doc-cn-ffmpeg/ffmpeg-doc-cn-02.md