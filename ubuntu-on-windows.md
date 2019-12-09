---
description: 種種解決的過程...
---

# Ubuntu on windows

#### \#ubuntu github位置

```text
cd /mnt/c/Users/MMN-AI/Documents/GitHub
```

#### \#解決ubuntu on windows 無法呈現matplotlib的plt功能

最有用的解法:

{% embed url="http://k28h.blogspot.com/2018/04/wsl-windowslinuxmatplotlib.html" %}

1. 安裝xming

2. 裝個x11-apps

```text
sudo apt-get install x11-apps
```

3. 添加環境變量

先打開bashrc

```text
vim ~/.bashrc
```

在最後加上這行

```text
export DISPLAY=localhost:0.0
```

讓他source一下

```text
source ~/.bashrc
```

4. 裝個GTK

```text
sudo apt-get install gnome-calculator
```

5. 在要跑的腳本前面加上backend的指定'TkAgg'

```text
import matplotlib as mpl
mpl.use('TKAgg')
```

6. 應該就能跑圖了，不能跑起來的話就手動雙擊xming，開啟他

![](.gitbook/assets/image%20%2833%29.png)

