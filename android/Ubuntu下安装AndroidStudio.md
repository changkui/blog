写在前面
====
接触Ubuntu已经有一段时间了，对于使用Ubuntu进行程序开发，在爽不过了，接下来把自己学习的Android-studio在Ubuntu系统下的安装过程记录下来，进行习惯性的记忆

步骤
==
第一步：安装JDK
---------
打开终端
使用快捷键：Ctrl+Alt+T

使用如下三条命令，安装JDK
--------------
```
sudo add-apt-repository ppa:webupd8team/java 
sudo apt-get update 
sudo apt-get install oracle-java8-installer 
```
按照上面三条指令进行以此安装
![1](https://user-images.githubusercontent.com/29434858/51580232-c2c92780-1efe-11e9-9e5c-9578e8da47e6.png)
![2](https://user-images.githubusercontent.com/29434858/51580236-c8267200-1efe-11e9-9ef5-488282287a2b.png)
![3](https://user-images.githubusercontent.com/29434858/51580241-cceb2600-1efe-11e9-81ca-359206f4d337.png)
![4](https://user-images.githubusercontent.com/29434858/51580245-cfe61680-1efe-11e9-92d3-123e916ed920.png)

按照命令依次安装，如图所是，证明你就安装成功拉，嘻嘻！

检验JDK是否安装成功
-----------
输入：

    java -version
![5](https://user-images.githubusercontent.com/29434858/51580256-d83e5180-1efe-11e9-8e10-c443cbd01196.png)

安装AndroidStudio
===============

下载AndroidStudio
---------------
打开“https://developer.android.google.cn/studio/“链接，下载AndroidStudio

![6](https://user-images.githubusercontent.com/29434858/51580262-deccc900-1efe-11e9-8cb0-ccfb7caad983.png)

解压AndroidStudio
---------------
将Android复制到某个位置，并执行unzip指令解压
![7](https://user-images.githubusercontent.com/29434858/51580272-e68c6d80-1efe-11e9-9405-fb0cef0c77a7.png)


将解压好的文件移动到指定位置

本文移动到：/home/zhengzhuang/software 下
![8](https://user-images.githubusercontent.com/29434858/51580287-f2782f80-1efe-11e9-897b-3a39aff62c38.png)

打开终端，cd进入android-studio/bin目录“./studio.sh”进行安装
----------------------------------------------
![9](https://user-images.githubusercontent.com/29434858/51580298-f86e1080-1efe-11e9-8118-b6e457f7cbc5.png)


其他配置如Windows
------------

设置使用之前配置
![10](https://user-images.githubusercontent.com/29434858/51580303-fe63f180-1efe-11e9-8b8a-7db829f85a98.png)

设置是否代理，我选择取消
![11](https://user-images.githubusercontent.com/29434858/51580315-0459d280-1eff-11e9-9f97-64068c3ee128.png)

安装向导，依次按照步骤安装
----
![12](https://user-images.githubusercontent.com/29434858/51580335-0cb20d80-1eff-11e9-9333-71a2f1146757.png)
![13](https://user-images.githubusercontent.com/29434858/51580339-0e7bd100-1eff-11e9-82d0-7e62ac242f14.png)
![14](https://user-images.githubusercontent.com/29434858/51580341-10459480-1eff-11e9-990f-b251afd28457.png)
![15](https://user-images.githubusercontent.com/29434858/51580345-12a7ee80-1eff-11e9-95d1-3281bdbbee9f.png)
![16](https://user-images.githubusercontent.com/29434858/51580346-13d91b80-1eff-11e9-872c-a693e7af4e88.png)
![17](https://user-images.githubusercontent.com/29434858/51580347-15a2df00-1eff-11e9-8bf2-9fd2ee7c7d38.png)

到此步骤，就大功告成啦，开始新建项目吧！

新建项目
----