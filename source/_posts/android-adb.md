---
layout:     post
title:      "adb操作命令详解及大全"
date:       2017-09-08 9:13:00
author:     "Crazy江"
categories:
  - Android - 基础
tags: 
  - Android
  - adb
  - 命令

---


ADB，即 Android Debug Bridge，Android调试桥，身为 Android 开发的我们，熟练使用 ADB 命令将会大大提升我们的开发效率， ADB 的命令有很多，今天就来总结下我在开发常用到的一些 ADB 命令。

## 查看版本
```
$ adb version
```

## 查看连接设备
```
$ adb devices
```

## 安装apk
```
$ adb install <apkfile>
$ adb install -r <apkfile>   --保留数据和缓存文件，重新安装apk
$ adb install -s <apkfile>   --安装apk到sd卡
```

## 卸载apk
```
$ adb uninstall <packagename>
$ adb uninstall -k <packagename> --卸载 app 但保留数据和缓存文件
```

## 查看已安装
```
$ adb shell pm list packages
$ adb shell pm list packages -s   --系统应用的所有包名
$ adb shell pm list packages -3   --除了系统应用的第三方应用包名
```

## 清除应用数据及缓存
```
$ adb shell pm clear <packagename>
```

## 启动应用
```
$ adb shell am start -n com.test.demo/.ui.SplashActivity
```

## 强制停止应用
```
$ adb shell am force-stop <packagename>
```

## 查看日志
```
$ adb logcat
```

## 重启
```
$ adb reboot
```

## 获取序列号
```
$ adb get-serialno
```

## 获取 MAC 地址
```
$ adb shell  cat /sys/class/net/wlan0/address
```

## 查看设备型号
```
$ adb shell getprop ro.product.model
```

## 查看 Android 系统版本
```
$ adb shell getprop ro.build.version.release
```

## 查看屏幕分辨率
```
$ adb shell wm size
```

## 查看屏幕密度
```
$ adb shell wm density
```

## 进程状态
```
$ adb shell ps      -- ps: process status
```