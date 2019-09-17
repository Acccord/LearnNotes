## 一、为什么需要启动模式

在Android开发中，我们都知道，在默认的情况下，如果我们启动的是同一个Activity的话，系统会创建多个实例并把它们一一放入任务栈中。当我们点击返回（back）键，这些Activity实例又将从任务栈中一一移除，遵循的原则是“后进先出”（先进后出）。

这里我们考虑一个问题，当我们多次启动同一个Activity，系统也会创建多个实例放入任务栈中，这样岂不是很耗费内存资源？为了解决这一问题，Android为Actiivty提供了启动模式。

Activity的启动模式有四种：standard、singleTop、singleTask和singleInstance。

