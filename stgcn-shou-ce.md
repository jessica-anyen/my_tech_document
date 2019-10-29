---
description: 一樣是奮鬥很久的過程....
---

# st-gcn手冊

{% hint style="info" %}
190917更新

label\_name.txt檔 中的動作名稱可以更改

190910更新

這套工具的原理，中文版文件: [https://www.leiphone.com/news/201802/sSRbW4I2M4HheARj.html](https://www.leiphone.com/news/201802/sSRbW4I2M4HheARj.html)

這套工具可定義出來的動作清單 路徑:

C:\Users\MMN-AI\Documents\GitHub\st-gcn\resource\kinetics\_skeleton\label\_name.txt
{% endhint %}



最有幫助的參考文件

{% embed url="https://www.twblogs.net/a/5c98d377bd9eee491b626382" %}

st-gcn github

{% embed url="https://github.com/open-mmlab/mmskeleton" %}

### 1.openpose 安裝

有關安裝請看openpose手冊，假設你已經裝好了也clone了st-gcn，接下來請完成:

1.把生成的build/bin文件夾下的所有庫複製到x64/release

2.將models文件夾複製到build中

3.把440000模型放到coco中

4400000 openpose位置: C:\Users\MMN-AI\Documents\GitHub\openpose\models\pose\coco

放到st-gcn的位置: C:\Users\MMN-AI\Documents\GitHub\st-gcn\models\pose\coco

### 2.st-gcn的部分

因為我裝的環境是windows，所以要改一些地方

1.將demo\_old.py中的

\(因為使用上是分析已經載好的影片，所以使用demo\_old。原文所寫的是demo.py，但我那包沒有那個東西...

```text
#        openpose = '{}/examples/openpose/openpose.bin'.format(self.arg.openpose)此行改爲
        openpose = '{}/OpenPoseDemo.exe'.format(self.arg.openpose)
```

2.parser.add\_argument\('--openpose'改爲（建議要改，改了命令行就可以不輸入路徑直接默認值）

```text
parser.add_argument('--openpose',
            default='C:\Users\MMN-AI\Documents\GitHub\openpose\build1\x64\Release',
 ​           #路徑是OpenPoseDemo存在的位置
            help='Path to openpose')
```

### 3.執行時所需套件

這邊我裝了anaconda\(雖然很笨重，但是還是裝一下比較好，不要鐵齒...之前用miniconda也沒成功，用這個就好了

執行過程會提示缺少的套件，在anaconda找找裝上就可以了。比較會有問題的是pytorch和torchvision，可參考windows如何裝這兩個套件的文件。

建了一個環境叫nowpy3，執行時務必先切到這個環境



![](.gitbook/assets/image%20%2824%29.png)

按下這個run鍵，選擇"open terminal"

![](.gitbook/assets/image%20%2830%29.png)

前面的括號代表環境，可以確定現在的環境是nowpy3

![](.gitbook/assets/image%20%2810%29.png)

先切換路徑到專案底下

```text
cd /d C:\Users\MMN-AI\Documents\GitHub\st-gcn
```

執行

--video 你放要分析影片的路徑\(不用加' '，會錯

```text
python main.py demo_old  --video C:/Users/MMN-AI/Documents/GitHub/st-gcn/resource/media/clean_and_jerk.mp4
```

整個分析過程請耐心讓他跑...不會太快

看到這個就代表python的api有跑成功

![](.gitbook/assets/image%20%287%29.png)

看到這個就代表分析動作的結果生成了

prediction result代表他判斷這部影片的人在做甚麼，人可能有很多動作，但他只會顯示他覺得最有可能的一個

Saving下面有分析結果影片的位置

* 各影格人體姿勢json位置:

```text
C:\Users\MMN-AI\Documents\GitHub\st-gcn\data\openpose_estimation\snippets
```

* 產出結果影片位置:

```text
C:\Users\MMN-AI\Documents\GitHub\st-gcn\data\openpose_estimation\data
```

![](.gitbook/assets/image%20%2811%29.png)

分析結果的影片檔案比較大，使用windows的player打不開，需要右鍵&gt;使用其他媒體播放器

![](.gitbook/assets/image%20%2828%29.png)

### 結果

可以從右下方看到，雖然過程有預測人物在做其他動作，但最後只會有一個voting result，也就是人物在做什麼的結論

![](.gitbook/assets/image%20%2819%29.png)

嗯...雖然有些結果還是非常怪@@ \(這部片的人物在走路，但卻推論成在擲硬幣

![](.gitbook/assets/image%20%2826%29.png)

{% hint style="info" %}
0916後續補充
{% endhint %}

後續又有持續更新的版本，新的指令為

```text
mmskl
```

請改用

```text
python run.py
```



