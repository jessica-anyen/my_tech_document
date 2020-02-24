# openvino classroom c++ 安裝教學

1. 先照這篇的說明安裝好openvino\(注意：解壓縮請用指令，手動解開會有問題\)

[https://docs.openvinotoolkit.org/2020.1/\_docs\_install\_guides\_installing\_openvino\_linux.html\#install-external-dependencies](https://docs.openvinotoolkit.org/2020.1/_docs_install_guides_installing_openvino_linux.html#install-external-dependencies)

參考指令

```text
#啟用圖形化介面安裝
sudo ./install_GUI.sh
#切換到預設安裝的路徑
cd /opt/intel/openvino/install_dependencies/
#將openvino環境開啟(這一步美重開一個終端機都要做)
source /opt/intel/openvino/bin/setupvars.sh
#到build_demos.sh所在的路徑下(每台電腦路徑不同，要找)
cd /opt/intel/openvino/inference_engine/demos/
#建立範例檔案
./build_demos.sh
#建立成功後會自動出現omz_demos，切換到路徑下
cd /home/mmn/omz_demos_build/intel64/Release
#找到smart_classroom檔案
```

2.  下載所需pre-train model，網址:

[https://download.01.org/opencv/2020/openvinotoolkit/2020.1/open\_model\_zoo/models\_bin/1/](https://download.01.org/opencv/2020/openvinotoolkit/2020.1/open_model_zoo/models_bin/1/)

下載完建議可將各模型放置於models資料夾\(另外建立\)

了解每一個pre-train模型的內容（看他的readme）

[https://github.com/opencv/open\_model\_zoo/tree/master/models/intel](https://github.com/opencv/open_model_zoo/tree/master/models/intel)

3. 根據需要組出指令\(參考smart\_classroom網址介紹\)

{% embed url="https://docs.openvinotoolkit.org/2019\_R1/\_inference\_engine\_samples\_smart\_classroom\_demo\_README.html" %}

其中臉部辨識模型嘗試起來有問題，但該選項非必要

參考指令:

```text
#說明:
-m_act: 放動作辨識模型的位置
-m_lm: 放場景辨識的模型的位置
-out_v: 影片輸出的檔名、副檔名及位置
-i :要讓系統讀的檔案位置
```

```text
./smart_classroom_demo -m_act models/person-detection-action-recognition-0005.xml \
                       -m_lm models/landmarks-regression-retail-0009.xml \
                       -out_v videos/mktest1.avi \
                       -i videos/mktest1.mp4 
```

## \#結果

可發現雖然只有站著跟坐著兩種動作，但是判斷效果一般。例如:只有照到半身的畫面會自動判斷為"坐著"，靠太近的人也無法判斷

[https://drive.google.com/file/d/1mMhZAYXw4z32jRwqYFGR94ODmGsMRxEM/view?usp=sharing](https://drive.google.com/file/d/1mMhZAYXw4z32jRwqYFGR94ODmGsMRxEM/view?usp=sharing)

## \#參考文件

官方教學文件

{% embed url="https://docs.openvinotoolkit.org/2019\_R1/\_inference\_engine\_samples\_smart\_classroom\_demo\_README.html" %}

openvino工具包安裝

[https://chtseng.wordpress.com/2019/01/21/intel-openvino%E4%BB%8B%E7%B4%B9%E5%8F%8A%E6%A8%B9%E8%8E%93%E6%B4%BE%E3%80%81linux%E7%9A%84%E5%AE%89%E8%A3%9D/](https://chtseng.wordpress.com/2019/01/21/intel-openvino%E4%BB%8B%E7%B4%B9%E5%8F%8A%E6%A8%B9%E8%8E%93%E6%B4%BE%E3%80%81linux%E7%9A%84%E5%AE%89%E8%A3%9D/)

