
- [将图片转成mp4](#将图片转成mp4)
- [mp4转成ts,再拼接ts组合生成长mp4](#mp4转成ts再拼接ts组合生成长mp4)
- [查看多媒体的基本信息](#查看多媒体的基本信息)

# 将图片转成mp4
```
只要ffmpeg -i input.jpg output.mp4 即可将一个jpg图片转成mp4文件

ffmpeg -r 25 -loop 1 -i ship.png -pix_fmt yuv420p -vcodec libx264 -b:v 600k -r:v 25 -preset medium -crf 30 -s 600x480 -vframes 250 -r 25 -t 1 1.mp4 

其中ffmpeg -r 25 为读取输入文件的时候帧率为25帧每秒
-loop为循环读取input文件
以后面的内容就好理解了
其实关键的是-t 10，将这个jpg文件生成为10秒钟的mp4视频文件
```

# mp4转成ts,再拼接ts组合生成长mp4
```
将 mp4 文件封装为 ts 格式
ffmpeg -i a1.mp4 -vcodec copy -acodec copy -vbsf h264_mp4toannexb 1.ts

# 拼接 ts 并导出最终 mp4 文件
ffmpeg -i "concat:1.ts|2.ts|3.ts|4.ts" -acodec copy -vcodec copy -absf aac_adtstoasc output.mp4

```

# 查看多媒体的基本信息
```
ffprobe -select_streams v -show_entries format=duration,size,bit_rate,filename -show_streams -v quiet -of csv="p=0" -of json -i test.mp4
```


