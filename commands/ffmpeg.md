# ffmpeg常用指令

## 截取视频

```bash
ffmpeg -i input.mp4 -ss 00:00:10 -to 00:00:20 -c copy output.mp4
```



## 调整fps

```bash
-r target_fps
```

