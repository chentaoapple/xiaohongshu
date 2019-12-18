#### 数据测量

##### 1.Systrace

https://www.jianshu.com/p/c61307e79ac2



##### 1. gfxinfo

可以输出包含各阶段的动画以及帧相关的性能分析，具体命令如下：

```java
adb shell dumpsys gfxinfo packageName
```

在Android 6.0之后，gfxinfo命令新增了framestats参数，可以拿到最近120帧每个绘制阶段耗时信息

```java
adb shell dumpsys gfxinfo packageName framestats
```



##### 2.SurfaceFlinger

查看渲染使用的内存情况

```java
adb shell dumpsys SurfaceFlinger
```

