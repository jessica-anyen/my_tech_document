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





\`\`

