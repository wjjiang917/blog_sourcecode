---
layout:     post
title:      "Hexo+oschina，免费拥有自己的博客"
date:       2017-08-05 12:00:00
updated:    2017-09-06 14:46:00
author:     "Crazy江"
header-img: "hexo.jpg"
categories:
  - 随笔
tags: 
  - Hexo
  - oschina
  - gitee

---

## 博客搭建
[博客搭建教程](http://blog.csdn.net/qq_20954959/article/details/54425916)

推荐主题：[Next Theme](https://github.com/iissnan/hexo-theme-next)   [Next主题使用教程](http://theme-next.iissnan.com/getting-started.html)

## 开始写博客
* 学会写Markdown
* Hexo目录结构
![目录结构](http://ovu5hb0jj.bkt.clouddn.com/hexo.png-oschina)
    * _config.yml 配置文件
    * public 生成的页面HTML/JS/CSS
    * source/_posts 放入你的博客
    * 网站主题，可以使用[Hexo官网](https://hexo.io)提供的[博客网站主题模版](https://hexo.io/themes/)
* 在source/_posts目录下新增/修改博客或者修改任何配置文件后，
    * 执行命令生成页面
        ```
        hexo g(enerate)
        ```
    * 代码提交到Git仓库
        ```
        hexo d(eploy)
        ```
    * 也可以启动本地服务，预览博客
        ```
        hexo s(erver)
        ```
        

**PS**: 图片可以上传到*七牛云*存储
![Git](http://ovu5hb0jj.bkt.clouddn.com/git.jpg-oschina)
