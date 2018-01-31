---
layout:     post
title:      "Android Context笔记"
date:       2016-09-25 10:00:00
author:     "Crazy江"
categories:
  - Android - 基础
tags:
  - Context
  - Android

---


## Context是？
```
Interface to global information about an application environment. 
This is an abstract class whose implementation is provided by the Android system. 
It allows access to application-specific resources and classes, 
as well as up-calls for application-level operations such as launching activities, 
broadcasting and receiving intents, etc
```
> Context个数 ＝ 1\(Application\) + Activity个数 + Service个数

## Context应用场景
* **Application**：一个应用在创建的时候只会创建一个ActivityThread主线程，而在初始化ActivityThread主线程的时候就会创建一个Application对象。Application是全局的，在Activity和Service里都可以调用getApplication方法来获得一个应用的Application对象。Application的父类是ContextWrapper类。
* **Service**：Service父类是ContextWrapper，一个应用每创建一个Service，都会创建一个ContextImpl类去关联Service。
* **Activity**：Activity父类是ContextThemeWrapper，而ContextThemeWrapper父类是ContextWrapper。ContextThemeWrapper类是其父类的扩张，里面额外添加了关于主题设置的一些方法。在ActivityThread主线程中创建Activity的时候我们知道，创建完了Activity之后会立马调用Activity#setTheme设置Activity的主题。

## getApplication和getApplicationContext区别
>Read The Fucking Source Code 
<p style="text-align:right">-- Linus Benedict Torvalds</p>