---
layout:     post
title:      "Git命令"
date:       2017-09-07 13:41:00
author:     "Crazy江"
categories:
  - 笔记
tags: 
  - Git
  - 命令

---


## 将本地目录上传到远程仓库
```
$ git init
$ git add .
$ git commit -am "###"
$ git remote add origin https://gitee.com/wjjiang/CustomView.git
$ git pull --rebase origin master
$ git push origin master
```

## 查看代码修改的内容
```
$ git diff <file>  --比较某文件与最近提交节点的差异
$ git diff <hashcode> <hashcode> <file>   --比较某文件在提交节点a，节点b的差异
```

## 撤销本地修改
```
$ git checkout -- <file>
```