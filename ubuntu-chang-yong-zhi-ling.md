# ubuntu常用指令

查看ubuntu版本

```text
lsb_release -a
```

查看顯卡版本

```text
nvidia-smi
nvidia-smi-L
```

當conda activate無效

```text
#來源
https://www.jianshu.com/p/cd0096b24b43

# 激活环境
source activate
# 退出环境
source deactivate
```

影片剪輯

```text
openshot-qt
```

多檔案合併

```text
ffmpeg -f concat -safe 0 -i filelist.txt -c copy merge.mp4
/* 
1. filelist.txt 當中須以以下格式紀錄要合併的檔案（按順序)
file和檔名之間有空格

file '00M38S_1592452838.mp4'
file '01M38S_1592452898.mp4'

2.merge.mp4 是輸出檔名
*/
```

檔案分割（mp4分割後會變得不能用...

```text
split -n 4 making06.MP4 "making06.MP4.part"
/*
-n:均分
4:分成幾份
making06.MP4：要分割的檔案
"making06.MP4.part"：分割後的檔名
*/
```

