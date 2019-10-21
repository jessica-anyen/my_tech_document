# mmskeleton 安裝過程

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

![](.gitbook/assets/image%20%2820%29.png)

安裝pycocotools成功，但後面還是有問題...











### 參考文件

{% embed url="https://www.cnblogs.com/whlook/p/6974174.html" %}

{% embed url="https://blog.csdn.net/Suii\_v5/article/details/73550270" %}

位址問題: ​

[https://blog.csdn.net/caibaoH/article/details/78335094](https://blog.csdn.net/caibaoH/article/details/78335094)
