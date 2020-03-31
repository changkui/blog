### Flutter创建插件详解并发布到Pub库

#### 创建Flutter Plugin插件项目

#### （1）使用Android Studio创建项目

<img src='/Users/zhengzhuang/Library/Application Support/typora-user-images/image-20200331161158331.png' width='500' alt='android studio 创建插件项目' />

#### （2）使用`flutter create`命令行创建

```dart
flutter create --org com.awei --template=plugin -a java --description "A Flutter plugin for using devices informations in Android" flutter_device_information
```

常用的命令参数如下：

- --org：定义项目的组织结构
- -a：用什么语言编写Android代码
- --description：插件的描述
- -i：用什么语言编写iOS代码

上面那个命令的意思是：创建一个插件，包名为“com.awei”，指定Android代码使用Java语言编写，插件项目名称为“flutter_device_information”，项目描述为：“A Flutter plugin for using devices informations in Android”。

<img src='https://upload-images.jianshu.io/upload_images/6098829-378c8ff66e6b945d.png' width='400' alt='完整的项目结构' />

到这里项目创建完成，接下来就是进行项目插件的开发工作，这里就不做进行详细的介绍，等项目创建完成之后接下来就是上传到github仓库中

到这里其实自己写的插件是可以用的，使用方法在`pubspec.yaml`文件中直接写入

```dart
dependencies:
  rain:
    git: https://github.com/zhengzhuang96/flutter_eui.git
```



#### 将项目发布到pub中

带项目编写完成并无bug的时候，这个时候可以上传到pub中使用，这个过程中首先保证你的终端可以翻墙，然后还有一个谷歌邮箱账号

先在根目录文件`pubspec.yaml`中顶部写入自己插件的信息

```dart
name: rain
description: 轻量、可靠的移动端 Flutter 组件库
version: 0.0.1
homepage: https://github.com/zhengzhuang96/rain.git
```

编写好之后根目录下运行命令，进行发布

```dart
flutter packages pub publish --server=https://pub.dartlang.org
```

运行之后显示`Look greate! Are you ready to upload your package（y/n）?`证明并无问题是否发布，输入y

<img src='/Users/zhengzhuang/Library/Application Support/typora-user-images/image-20200331145358750.png' width='500' alt='android studio 创建插件项目' />

它会让你去进行账号授权，复制它给你的连接放到浏览器中进行授权，这里就需要翻墙了，授权成功出现下面的结果就证明成功，然后等待上传

![image-20200331145619616](/Users/zhengzhuang/Library/Application Support/typora-user-images/image-20200331145619616.png)

等待上传会很慢，这里要是一只卡住，说明你的终端没有翻墙成功

![image-20200331145609390](/Users/zhengzhuang/Library/Application Support/typora-user-images/image-20200331145609390.png)

等一切上传之后出现`Successfully uploaded package.`证明上传成功

![image-20200331163516059](/Users/zhengzhuang/Library/Application Support/typora-user-images/image-20200331163516059.png)

当你上传成功之后，在`https://pub.flutter-io.cn/`中不能瞬间出现的，需要大约等20分钟时到1小时左右，才能搜索到，其实上传成功之后就不用等待了，直接可以在项目中使用

```dart
dependencies:
  rain:
    git: 0.0.1
```

大功告成！！！

