---
title: Thread 01 - 线程及其状态
date: 2024-03-01
slug: thread/thread-states
image: img/2024/03/Porcini.jpg
categories: [Learning]
tags: [Learning, Thread]
---

## 线程概述

Java 线程是 Java 中实现**并发（concurrency）** 和 **并行（parallelism）** 编程的基础。线程是程序中不同执行路径的最小单元，它允许你同时进行多项任务。

## 线程的创建

### 继承 Thread 类

通过继承 **Thread** 类并覆盖它的 **run()**  方法来创建一个线程。然后，创建该类的实例，并调用它的 **start()** 方法来启动线程。

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running.");
    }

    public static void main(String args[]) {
        MyThread t1 = new MyThread();
        t1.start(); // 启动线程
    }
}
```

### 实现 Runnable 接口

另一种创建线程的方式是实现 **Runnable** 接口并将其实例传递给 **Thread** 类的构造器。这种方式更灵活，因为 Java 不支持多重继承，但可以实现多个接口。

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Thread is running.");
    }

    public static void main(String args[]) {
        MyRunnable myRunnable = new MyRunnable();
        Thread thread = new Thread(myRunnable);
        thread.start(); // 启动线程
    }
}
```

### 总结

随着Java 并发各种工具的完善，其实创建线程的方法还有很多，比如使用**线程池**，**CompletableFuture**异步任务等。这些只是封装了高级的API，其本质还是离不开上面的两种方式。或者
更简化的说，使用线程执行任务，必须满足两点：

* 要有 **Thread** 类的实例
* 要执行的任务放到 **run()** 方法内。



## 线程的生命周期

* **NEW**：创建后尚未启动的线程。
* **Runnable**：可能正在运行，也可能正在等待 CPU 分配时间片。
* **Blocked**：等待监视器锁，试图进入一个被其他线程锁定的同步块。
* **Waiting**：等待其他线程执行特定操作。
* **Timed Waiting**：在指定的时间内等待。
* **Terminated**：线程的运行结束。


## 线程状态的转换

## Thread类常用的方法

### 构造方法

```java
    public Thread() {
        init(null, null, "Thread-" + nextThreadNum(), 0);
    }


    public Thread(Runnable target) {
        init(null, target, "Thread-" + nextThreadNum(), 0);
    }


    Thread(Runnable target, AccessControlContext acc) {
        init(null, target, "Thread-" + nextThreadNum(), 0, acc, false);
    }


    public Thread(ThreadGroup group, Runnable target) {
        init(group, target, "Thread-" + nextThreadNum(), 0);
    }


    public Thread(String name) {
        init(null, null, name, 0);
    }


    public Thread(ThreadGroup group, String name) {
        init(group, null, name, 0);
    }


    public Thread(Runnable target, String name) {
        init(null, target, name, 0);
    }


    public Thread(ThreadGroup group, Runnable target, String name) {
        init(group, target, name, 0);
    }


    public Thread(ThreadGroup group, Runnable target, String name,
                  long stackSize) {
        init(group, target, name, stackSize);
    }
```