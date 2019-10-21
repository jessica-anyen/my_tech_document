---
description: 當你成功的安裝完成以後....
---

# openpose運行操作

{% hint style="info" %}
0926更新:影片儲存指令

--write\_video name.avi ，預設存在openpose目錄下，可用放大鏡找檔案名比較快 
{% endhint %}

{% hint style="info" %}
0827更新:重新bulid了一次，這次執行方法可用以下語法執行

```text
python 1_body_from_image.py
```
{% endhint %}

{% hint style="info" %}
先打開power shell\(windows+x再按a\)再開始
{% endhint %}

### 1.手指的部分

video.mp4請改成需要的檔案名稱

```text
build\x64\Release\OpenPoseDemo.exe --video examples\media\video.mp4 --face --hand
```

**結果**

跑起來超慢\(應該是一禎一秒...要提前終止請按esc\)、側面的手指找不出來

![](.gitbook/assets/image%20%2813%29.png)

不一定要顯現10隻手指也可以找到

![](.gitbook/assets/image%20%2811%29.png)

### 2.輸出

{% embed url="https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/master/doc/output.md" %}

{% embed url="https://blog.csdn.net/lgh0824/article/details/76737032" %}

目前試成功的處理方法\(會儲存成yml格式，xml跟json無法存\)\(examples\media\_weuse\ 請改成實際放影像的地方，media\_out是放匯出資料的地方\)

以json格式儲存: write json

```text
build\x64\Release\OpenPoseDemo.exe --image_dir examples\media_weuse\ --write_json examples\media_out\
```

以yml格式儲存:write keypoint

```text
build\x64\Release\OpenPoseDemo.exe --image_dir examples\media_weuse\ --write_keypoint examples\media_out\
```

#### **肢體位置對照表**

\#body 25

![](.gitbook/assets/image%20%286%29.png)

| 代號/順序 | 部位 |
| :--- | :--- |
| 0 | 脖子頭接合處 |
| 1 | 鎖骨正中心 |
| 2 | 對象右肩關節 |
| 3 | 對象右肘關節 |
| 4 | 對象右手腕 |
| 5 | 對象左肩關節 |
| 6 | 對象左肘關節 |
| 7 | 對象左手腕關節 |
| 8 | 對象髖關節正中 |
| 9 | 對象右髖 |
| 10 | 對象右膝關節 |
| 11 | 對象右踝關節 |
| 12 | 對象左髖 |
| 13 | 對象左膝關節 |
| 14 | 對象左踝關節 |
| 15 | 對象右眼 |
| 16 | 對象左眼 |
| 17 | 對象右臉 |
| 18 | 對象左臉 |
| 19 | 對象左腳尖 |
| 20 | 對象左腳趾 |
| 21 | 對象左腳後跟 |
| 22 | 對象右腳尖 |
| 23 | 對象右腳趾 |
| 24 | 對象右腳跟 |

