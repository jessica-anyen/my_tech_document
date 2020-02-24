# openvino classroom c++ 安裝教學

1. 先照這篇的說明安裝好openvino\(注意：解壓縮請用指令，手動解開會有問題\)

[https://docs.openvinotoolkit.org/2020.1/\_docs\_install\_guides\_installing\_openvino\_linux.html\#install-external-dependencies](https://docs.openvinotoolkit.org/2020.1/_docs_install_guides_installing_openvino_linux.html#install-external-dependencies)

參考指令



![](.gitbook/assets/image%20%2825%29.png)

```text
#啟用圖形化介面安裝
sudo ./install_GUI.sh
#切換到預設安裝的路徑
cd /opt/intel/openvino/install_dependencies/
#將openvino環境開啟(這一步美重開一個終端機都要做)
source /opt/intel/openvino/bin/setupvars.sh
#
cd /
```



## \#參考文件

官方教學文件

{% embed url="https://docs.openvinotoolkit.org/2019\_R1/\_inference\_engine\_samples\_smart\_classroom\_demo\_README.html" %}

openvino工具包安裝

[https://chtseng.wordpress.com/2019/01/21/intel-openvino%E4%BB%8B%E7%B4%B9%E5%8F%8A%E6%A8%B9%E8%8E%93%E6%B4%BE%E3%80%81linux%E7%9A%84%E5%AE%89%E8%A3%9D/](https://chtseng.wordpress.com/2019/01/21/intel-openvino%E4%BB%8B%E7%B4%B9%E5%8F%8A%E6%A8%B9%E8%8E%93%E6%B4%BE%E3%80%81linux%E7%9A%84%E5%AE%89%E8%A3%9D/)

