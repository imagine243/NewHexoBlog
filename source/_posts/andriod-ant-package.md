title: android使用ant打包
date: 2015-09-12 23:07:40
tags: Android 
tags: ant 
tags: package
categories : Android
---

### android使用ant打包
android 现在全方面都使用AndroidStudio，脚本打包也全面转向了使用 gradle， 官方的文档也全部都是gradle的。而现在的android游戏项目还是在使用eclipse，各种渠道，插件同样是eclipse的插件。所以记录下ant来打包android工程的方式。

### android环境
需要把 android命令，加入到环境变量中。
运行下面命令，查看下现在现在电脑上使用的androidsdk的版本。
>android list targets 

### 生成ant打包脚本。
进入android的工程目录
运行下面命令，生成ant打包脚本build.xml, num是刚刚获得的androidsdk版本。
>android update project --path . --target num 

### ant 打包
在android工程目录运行 ant，默认是help target
清理android工程

>ant clean
 
打包android工程

>ant package 
