---
title: JVM 01 - 类加载过程详解
date: 2024-02-26
slug: jvm/class-loading
image: img/2024/02/HippieTown.jpg
categories: [Learning]
tags: [Learning, JVM]
---


## 类的生命周期

类 **从被加载到虚拟机内存中开始到卸载出内存为止**，它的整个生命周期可以简单概括为 **7 个阶段**：**加载（Loading）**、**验证（Verification）**、**准备（Preparation）**、**解析（Resolution）**、**初始化（Initialization）**、**使用（Using）** 和 **卸载（Unloading）**。其中，**验证、准备和解析**这三个阶段可以统称为 **链接（Linking）**。

## 类加载过程

### 加载

类加载过程的第一步，主要完成下面 **3** 件事情：

* 通过**全类名**获取定义此类的**二进制字节流**。
* 将字节流所代表的**静态存储结构**转换为方法区的运行时数据结构。
* 在内存中生成一个代表该类的 **Class** 对象，作为方法区这些数据的访问入口。

