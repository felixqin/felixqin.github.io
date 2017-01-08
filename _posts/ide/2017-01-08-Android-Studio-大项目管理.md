---
layout: post
category : Android
tagline: "Supporting tagline"
tags : [Android, Android Studio, 教程, joyteam]
---



# Android Studio 大项目管理

Android Studio 本身一个工程可以管理多个项目，但是默认情况下创建的lib和app项目在同一个路径下。在大型工程下，各个lib需要分开管理，且可被多个app复用。本文描述如何构建可复用的lib项目。

[TOC]

## 目录规划

```
projects
	|- apps
		|- apk1
	|- libs
		|- lib1
		|- lib2
```



## 新建工程和库

### 创建 Android Studio 工程

选择 `projects/apps/apk1`目录保存工程

### 创建 lib1 库

菜单选择`File->New->New Module...`，弹出的对话框选择`Android Library`，根据向导创建 lib1。

### 资源管理器中整理目录

将 `projects/apps/apk1/lib1` 移动到 `projects/libs/lib1`

### 修改工程配置文件

- 修改`projects/apps/apk1/settings.gradle` include 内容 

```
include ':app'
include ':..:..:libs:lib1'
```

- 修改 `projects/apps/apk1/app/build.gradle`，dependencies 中 加入 compile project

```
dependencies {
    ...

    compile project(':..:..:libs:lib1')
}

```

- 改完成之后 Sync 工程

## 添加已存在的库

参考前述步骤，修改工程配置文件，将lib1替换成lib2，即可将 lib2 加入工程。


```
include ':app'
include ':..:..:libs:lib1'
include ':..:..:libs:lib2'
```


```
dependencies {
    ...

    compile project(':..:..:libs:lib1')
    compile project(':..:..:libs:lib2')
}
```
