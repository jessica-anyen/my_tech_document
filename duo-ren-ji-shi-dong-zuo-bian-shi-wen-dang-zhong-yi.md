---
description: Multi-person Real-time Action Recognition Based-on Human Skeleton
---

# 多人即時動作辨識\_文檔中譯

### \#演算法

1. 這個作品收集了九種姿勢

`['stand', 'walk', 'run', 'jump', 'sit', 'squat', 'kick', 'punch', 'wave']`

整個影片的總長度為20分鐘，包含10000個影格，每一秒有10個影格

整個作業流程如下:

1.先用openpose取得骨架位置\(joints' positions\)

2.追蹤每一個人，兩個骨架的歐氏距離是用來辨認兩個人\(見 [lib\_tracker.py](https://github.com/felixchenfy/Realtime-Action-Recognition/blob/master/utils/lib_tracker.py)\)

3.藉由前一影格補上遺失的關節點\(見 [lib\_feature\_proc.py](https://github.com/felixchenfy/Realtime-Action-Recognition/blob/master/utils/lib_feature_proc.py)\)

4. 對關節點增加噪音，試圖增廣資料

5. 設定window size =0.5秒\(5個影格\)，用以擷取特徵

6. 擷取特徵:1\)肢體速度 2\)正規化關節位置 3\)關節點速率

7. 使用PCA\(主元素萃取\)，降低維度到80，使用3層DNN，每層50個節點\(見  [lib\_classifier.py](https://github.com/felixchenfy/Realtime-Action-Recognition/blob/master/utils/lib_classifier.py)/class ClassifierOfflineTrain\)

{% hint style="info" %}
dnn 深度神經網路

[https://medium.com/%E4%B8%80%E4%BA%BA%E5%A4%9A%E5%B7%A5%E5%B7%A5%E4%BD%9C%E5%AE%A4/dnn-%E6%B7%B1%E5%BA%A6%E7%A5%9E%E7%B6%93%E7%B6%B2%E8%B7%AF-cf892cbb06d5](https://medium.com/%E4%B8%80%E4%BA%BA%E5%A4%9A%E5%B7%A5%E5%B7%A5%E4%BD%9C%E5%AE%A4/dnn-%E6%B7%B1%E5%BA%A6%E7%A5%9E%E7%B6%93%E7%B6%B2%E8%B7%AF-cf892cbb06d5)
{% endhint %}

8. 平均過濾兩影格之間的預測分數，當預測分數大於0.8的時候，添加標籤\(見  [lib\_classifier.py](https://github.com/felixchenfy/Realtime-Action-Recognition/blob/master/utils/lib_classifier.py) /class ClassifierOnlineTest

\#如何包含頭部節點?

在add\_cur\_skeleton函式中修改\(見  [utils/lib\_feature\_proc.py](https://github.com/felixchenfy/Realtime-Action-Recognition/blob/master/utils/lib_feature_proc.py)/ class FeatureGenerator/ def add\_cur\_skeleton\)

\#如何更換rnn分類器

1. 修改add\_cur\_skeleton，藉由前一骨架輸出
2. 修改 utils/lib\_classifier.py 當中的 `class ClassifierOfflineTrain` 中的\_\_init\_\_ 和 predict







