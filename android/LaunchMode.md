## 一、为什么需要启动模式

在Android开发中，我们都知道，在默认的情况下，如果我们启动的是同一个Activity的话，系统会创建多个实例并把它们一一放入任务栈中。当我们点击返回（back）键，这些Activity实例又将从任务栈中一一移除，遵循的原则是“后进先出”（先进后出）。

这里我们考虑一个问题，当我们多次启动同一个Activity，系统也会创建多个实例放入任务栈中，这样岂不是很耗费内存资源？为了解决这一问题，Android为Actiivty提供了启动模式。

Activity的启动模式有四种：standard、singleTop、singleTask和singleInstance。

## 二、启动模式的分类
### 1、standard：标准模式
这种启动模式为标准模式，也是默认模式。每当我们启动一个Activity，系统就会相应的创建一个实例，不管这个实例是否已经存在。这种模式，一个栈中可以有多个实例，每个实例也都有自己的任务栈。而且是谁启动了此Activity，那么这个Activity就运行在启动它的Activity所在的栈中。

### 2、singleTop：栈顶复用模式
这种启动模式下，如果要启动的Activity已经处于栈的顶部，那么此时系统不会创建新的实例，而是直接打开此页面，同时它的onNewIntent()方法会被执行，我们可以通过Intent进行传值，而且它的onCreate()，onStart()方法不会被调用，因为它并没有发生任何变化。

### 3、singleTask：站内复用模式
在这个模式下，如果栈中存在这个Activity的实例就会复用这个Activity，不管它是否位于栈顶，复用时，会将它上面的Activity全部出栈，因为singleTask本身自带clearTop这种功能。并且会回调该实例的onNewIntent()方法。其实这个过程还存在一个任务栈的匹配，因为这个模式启动时，会在自己需要的任务栈中寻找实例，这个任务栈就是通过taskAffinity属性指定。如果这个任务栈不存在，则会创建这个任务栈。不设置taskAffinity属性的话，默认为应用的包名。

### 4、singleInstance：单实例模式
单实例模式，顾名思义，只有一个实例。该模式具备singleTask模式的所有特性外，与它的区别就是，这种模式下的Activity会单独占用一个Task栈，具有全局唯一性，即整个系统中就这么一个实例，由于栈内复用的特性，后续的请求均不会创建新的Activity实例，除非这个特殊的任务栈被销毁了。以singleInstance模式启动的Activity在整个系统中是单例的，如果在启动这样的Activiyt时，已经存在了一个实例，那么会把它所在的任务调度到前台，重用这个实例。