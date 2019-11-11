---
description: Multi-person Real-time Action Recognition Based-on Human Skeleton
---

# 多人即時動作辨識

來源:

{% embed url="https://github.com/jessica-anyen/Realtime-Action-Recognition" %}

#### \#安裝注意事項:

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

#### \#跑完的結果

存放位置:

```text
C:\Users\MMN-AI\Documents\GitHub\r_a_r\output\exercise
```



