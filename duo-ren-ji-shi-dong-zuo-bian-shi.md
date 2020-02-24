---
description: Multi-person Real-time Action Recognition Based-on Human Skeleton
---

# 多人即時動作辨識

來源:

{% embed url="https://github.com/jessica-anyen/Realtime-Action-Recognition" %}

### \#安裝注意事項:

基本上按照readme進行安裝即可，環境請參考"ubuntu on windows"那篇的設定

要注意的地方:

1.  跑到這一行的時候，要在run.py指定backend才能跑圖

```text
cd $MyRoot/src/githubs/tf-pose-estimation
python run.py --model=mobilenet_thin --resize=432x368 --image=./images/p1.jpg
```

在run. py中加上

```text
import matplotlib as mpl
mpl.use('TKAgg')
```

才會正確跑出圖

#### \#安裝在ubuntu時的cuda+cudnn問題（cudnn初始化問題）

有可能會出現"UnknownError \(see above for traceback\): Failed to get convolution algorithm. This is probably because cuDNN failed to initialize, so try looking to see if a warning log message was printed above."錯誤訊息

解決方法：

```text
在腳本前添加：
# jc add for cudnn初始化問題
from tensorflow.compat.v1 import ConfigProto
from tensorflow.compat.v1 import InteractiveSession

config = ConfigProto()
config.gpu_options.allow_growth = True
session = InteractiveSession(config=config)
#
```

### \#demo

切換conda環境\(使用tf\)

```text
conda activate tf
```

影片

```text
python src/s5_test.py \
    --model_path model/trained_classifier.pickle \
    --data_type video \
    --data_path data_test/name.mp4 \
    --output_folder output
```

多張圖片

```text
python src/s5_test.py \
    --model_path model/trained_classifier.pickle \
    --data_type folder \
    --data_path data_test/file_name/ \
    --output_folder output
```

### \#跑完的結果

存放位置:

```text
C:\Users\MMN-AI\Documents\GitHub\r_a_r\output\exercise
```

#### -輸出影片的framerate調整

在config當中，s5設定的地方。output video\_fps即可調整\(但分析時frame rate一定要是10 fps，輸出影片是檢視用，所以可以不同\)

![](.gitbook/assets/image%20%2813%29.png)

#### \#demo影片

[https://drive.google.com/open?id=1zcTlurP5RjJeDYtTZJx1haB3\_QhfuxDz](https://drive.google.com/open?id=1zcTlurP5RjJeDYtTZJx1haB3_QhfuxDz)

#### \#限制

-不能使用單一張圖片，必須是連續影片

-一次需訓練識別兩種動作以上，例如:"dab"、"other"

-訓練資料需具多角度樣本，否則在識別過程中可能因為角度問題，導致識別失敗

### \#常見QA

1.人物id\(P??\)是由哪一支程式判斷?

ans:由s5\_test. py，dict\_id2clf 定義。但是畫面顯示上只會顯示最後一位\(例如:p176只會顯示p6\)，而且前面影格判斷出的部分不完全節點，會影響人物計數。

2.為何影片解析度建議為656x368?

ans:

因為姿勢辨識工具tf-pose使用cmu資料集，而cmu資料集使用656x368解析度訓練\(詳細可見tf-pose說明\)

3.frame 數與時間換算?

1秒15楨

