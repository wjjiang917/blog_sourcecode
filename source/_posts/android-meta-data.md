---
layout:     post
title:      "Android获取Manifest中<meta-data>元素的值"
date:       2017-09-08 17:24:00
author:     "Crazy江"
categories:
  - Android - 基础
tags: 
  - Android
  - meta-data

---

在AndroidManifest.xml中，<meta-data>元素可以作为子元素，被包含在<activity>、<application> 、<service>和<receiver>元素中，不同的父元素，在应用时读取的方法也不同。

## 在Activity应用<meta-data>元素
xml:

```xml
<activity...>
    <meta-data android:name="data_Name" android:value="hello my activity"></meta-data>
</activity>
```
java:

```java
ActivityInfo info = this.getPackageManager().getActivityInfo(getComponentName(), PackageManager.GET_META_DATA);
String msg = info.metaData.getString("data_Name");
```

## 在application应用<meta-data>元素
xml:

```xml
<application...>
    <meta-data android:name="data_Name" android:value="hello my application"></meta-data>
</application>
```
java:

```java
ApplicationInfo info = this.getPackageManager().getApplicationInfo(getPackageName(), PackageManager.GET_META_DATA);
String msg = info.metaData.getString("data_Name");
```

## 在service应用<meta-data>元素
xml:

```xml
<service android:name="MetaDataService">
    <meta-data android:value="hello my service" android:name="data_Name"></meta-data>
</service>
```
java:

```java
ComponentName cn = new ComponentName(this, MetaDataService.class);
ServiceInfo info = this.getPackageManager().getServiceInfo(cn, PackageManager.GET_META_DATA);
String msg = info.metaData.getString("data_Name");
```

## 在receiver应用<meta-data>元素
xml:

```xml
<receiver android:name="MetaDataReceiver">
    <meta-data android:value="hello my receiver" android:name="data_Name"></meta-data>
    <intent-filter>
        <action android:name="android.intent.action.PHONE_STATE"></action>
    </intent-filter>
</receiver>
```
java:

```java
ComponentName cn = new ComponentName(context, MetaDataReceiver.class);
ActivityInfo info = context.getPackageManager().getReceiverInfo(cn, PackageManager.GET_META_DATA);
String msg = info.metaData.getString("data_Name");
```
