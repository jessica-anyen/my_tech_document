# mmskeleton 安裝過程

#### \#docker使用

右下角--&gt;對小鯨魚右鍵--&gt;restart

![](.gitbook/assets/image%20%2817%29.png)

使用cmd或conda，於終端機輸入\(切換完後即可使用linux語法\):

```text
docker run -it -v /home:/mnt --shm-size 4G cheney0813/mmdetection /bin/bash
```

conda 環境切換

```text
conda activate mmdetection
```

如果要確定有甚麼image

```text
docker images
```

active完切換路徑

```text
cd /home/mmdetection
```

就可以繼續安裝了

-windows docker 安裝

[https://marcus116.blogspot.com/2019/01/docker-docker-for-windows.html](https://marcus116.blogspot.com/2019/01/docker-docker-for-windows.html)

-docker 環境切換

[https://marcus116.blogspot.com/2019/01/docker-image-operating-system-windows.html](https://marcus116.blogspot.com/2019/01/docker-image-operating-system-windows.html)

-使用docker安裝方法

[https://blog.csdn.net/cindy\_lxy/article/details/102631416](https://blog.csdn.net/cindy_lxy/article/details/102631416)

-mmdetection的docker容器pull方法\(激活環境方法，有用\)

[https://uzshare.com/view/781783](https://uzshare.com/view/781783)

----------------------------------------------------------------------------------------------------------------

windows使用要改的地方

-setup\_linux.py: 參考這篇"编译lib"處的改法

{% embed url="https://www.cnblogs.com/whlook/p/6974174.html" %}

註解掉第93行compiler\_so

```text
#default_compiler_so = self.compiler_so
```

-setup.py :將with open 段註解掉

這邊因為有位址寫入格式問題，讓他寫一次之後，會先報錯，然後註解掉再跑一次

這行的作用會產生一個version.py檔

```text
#with open(version_file, 'w') as f:
    #f.write(
     #   content.format(time.asctime(), VERSION, SHORT_VERSION,
      #                 MMSKELETON_HOME))
```

-跑完報錯那一次後，在version.py 這個檔案中，mmskl\_home這行的位址前面加個"r"

```text
mmskl_home = r'C:\Users\MMN-AI\Documents\GitHub\mmskeleton'
```

-確定有安裝c++套件\(使用visual studio installer 的修改功能，補安裝"c++桌面開發"的功能\)

![](.gitbook/assets/image%20%286%29.png)

-執行驗證

```text
python mmskl.py pose_demo
```

會出現問題:

![](.gitbook/assets/image%20%281%29.png)

這個要去安裝pycocotools

參考: [http://tn00343140a.pixnet.net/blog/post/203329451](http://tn00343140a.pixnet.net/blog/post/203329451)

-pycocotools安裝問題:

{% embed url="https://blog.csdn.net/chixia1785/article/details/80040172" %}

後來採用:直接註解掉" **/Wno-cpp"**相關的字

參考:[https://www.jianshu.com/p/de455d653301](https://www.jianshu.com/p/de455d653301)[https://www.jianshu.com/p/de455d653301](https://www.jianshu.com/p/de455d653301)

![](.gitbook/assets/image%20%2821%29.png)

安裝pycocotools成功，但後面還是有問題...











### 參考文件

{% embed url="https://www.cnblogs.com/whlook/p/6974174.html" %}

{% embed url="https://blog.csdn.net/Suii\_v5/article/details/73550270" %}

位址問題: ​

[https://blog.csdn.net/caibaoH/article/details/78335094](https://blog.csdn.net/caibaoH/article/details/78335094)

