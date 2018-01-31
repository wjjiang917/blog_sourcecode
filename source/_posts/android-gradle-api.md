---
layout:     post
title:      "android-apt、annotationProcessor、provided、compile和Gradle 3.X的指令api、implementation"
date:       2017-06-06 10:00:00
author:     "Crazy江"
categories:
  - Android - Gradle
tags:
  - Gradle
  - Android

---

## android-apt

APT(Annotation Processing Tool)，注释处理工具，对源代码文件进行检测，根据注解自动生成代码。并编译生成的源文件和原来的源文件，将它们一起生成class文件。

## annotationProcessor

编译时执行，不会打包到apk中。完全替代android-apt。

## provided
编译时执行，不会打包到apk中。但是跟apt/annotationProcessor有着根本的不同。

```
A 、B、C都是Library。 
A依赖了C，B也依赖了C 
App需要同时使用A和B 
那么其中A（或者B）可以修改与C的依赖关系为Provided
```

A这个Library实际上还是要用到C的，只不过它知道B那里也有一个C，自己再带一个就显得多余了，等app开始运行的时候，A就可以通过B得到C，也就是两人公用这个C。所以自己就在和B汇合之前，假设自己有C。如果运行的时候没有C，肯定就要崩溃了。

总结一下，Provided是间接的得到了依赖的Library，运行的时候必须要保证这个Library的存在，否则就会崩溃，起到了避免依赖重复资源的作用。

## compile
会编译到最后的APK或library中

## api
完全等同于compile指令

## implementation
对于使用了该命令编译的依赖，对该项目有依赖的项目将无法访问到使用该命令编译的依赖中的任何程序，也就是将该依赖隐藏在内部，而不对外部公开。

![api指令编译](http://ovu5hb0jj.bkt.clouddn.com/gradle-api.png-oschina)
![implementation指令编译](http://ovu5hb0jj.bkt.clouddn.com/gradle-implement.png-oschina)

## 建议

在Google IO 相关话题的中提到了一个建议，就是依赖首先应该设置为implement的，如果没有错，那就用implement，如果有错，那么使用api指令，这样会使编译速度有所增快。



***
## 参考资料

[android gradle tools 3.X 中依赖，implement、api 指令](http://blog.csdn.net/soslinken/article/details/73114637?utm_source=tuicool&utm_medium=referral)

[深入理解编译注解（三）依赖关系 apt/annotationProcessor与Provided的区别](http://blog.csdn.net/u011315960/article/details/64443910)

[你必须知道的APT、annotationProcessor、android-apt、Provided、自定义注解](http://blog.csdn.net/xx326664162/article/details/68490059)

[Android注解使用之注解编译android-apt如何切换到annotationProcessor](http://www.cnblogs.com/whoislcj/p/6148410.html)