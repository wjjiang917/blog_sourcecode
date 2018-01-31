---
layout:     post
title:      "Android避免资源被系统扫描并显示 - .nomedia"
date:       2016-09-05 10:00:00
author:     "Crazy江"
categories:
  - Android - 基础
tags:
  - nomedia
  - Android

---


## 背景
最近做的直播应用中，贴纸功能需要从服务器下载贴纸资源（含图片）。下载到本地后，会在相册中被列出来～  怎么做到不在相册中显示呢？ **.nomedia**

## 说明
这是 [官网](https://developer.android.com/guide/topics/data/data-storage.html?hl=zh-cn)对.nomedia的解释：
>在媒体扫描程序中隐藏您的文件在您的外部文件目录中包含名为 .nomedia
 的空文件（注意文件名中的点前缀）。 这将阻止媒体扫描程序读取您的媒体文件，并通过 [MediaStore](https://developer.android.com/reference/android/provider/MediaStore.html?hl=zh-cn)内容提供程序将其提供给其他应用。 但如果您的文件真正是应用的私有文件，则应该[将其保存在应用私有的目录中](https://developer.android.com/guide/topics/data/data-storage.html?hl=zh-cn#AccessingExtFiles)。

所以通过新建.nomedia文件还能阻止媒体扫描程序读取音频、视频和图片文件。

```Java
    File file = new File(filePath + "/.nomedia" );  
    if (!file.exists()){
        try {  
            file.createNewFile();  
        } catch (Exception e) {  
            e.printStackTrace();  
        }
    } 
```
<br>


***
*当然，你也能通过修改文件类型，改成系统不可认的类型即可；或者将上级目录修改为“.folderName”*