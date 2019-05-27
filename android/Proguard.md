# Proguard
## 混淆简介
1. Android代码混淆是一种应用源代码保护技术，用来防止别人对apk进行逆向分析；
2. 从Android2.3开始，Google就在SDK中加入了ProGuard的工具，使用它来进行代码的混淆。
3. ProGuard是一个压缩、优化和混淆Java字节码文件的免费工具， 其作用有以下几点：
- 删除代码中的注释；
- 删除代码中没有用到的类、字段、方法和属性；
- 会把代码中的包名、类名、方法名，变量名等修改为abcd...这种没有意义的名字，使得反编译出来的代    码难以阅读，从而达到防止apk被破解和逆向分析的目的；
- 经过ProGuard混淆后，apk安装包会变小；
4. 在实际项目中，有些Java类不能进行混淆，需要配置混淆规则；
5. 在实际项目中，打包apk时一般都需要进行混淆处理；
6. 混淆后会生成mapping.txt文件，该文件需要存档以便用来还原和查看混淆后的出错日志；

## 开启混淆
在项目的build.gradle文件中打开混淆的开关，然后在proguard-rules.pro文件中添加混淆规则即可
```
buildTypes {
        debug {
            //是否进行混淆
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        release {
            minifyEnabled true          //开启混淆只需要设置为true即可
            //添加混淆规则的位置
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
```
## 添加混淆规则
首先介绍一下添加混淆规则中常用到的一些命令的含义，方便我们理解并能够自行添加属于我们项目中的一些混淆规则，然后再介绍一下项目中一些通用的混淆规则。

### 1. 混淆规则常用到的命令含义：

- 保留该包下的类名不会被混淆，但是该包的子包的类名还是会被混淆
```
-keep class pageName.*
```

- 保留该包及其子包的类名不会被混淆
```
-keep class pageName.**
```

- 保留类名及其该类的内容不会被混淆（包括变量名，方法名等）
```
-keep class pageName.* {*;}
```

- 不保留类名只保留该类的方法名、变量名等不会被混淆
```
-keepclassmembers class pageName.*{*;}
```

- 保留所有继承某类的子类不会被混淆（implement同理）
```
-keep public class * extends android.app.Activity
```

- 保留该内部类中所有的public方法名、变量名不会被混淆
```
-keepclassmembers class pageName$内部类名 {//"$"的含义是保留某类的内部类不会被混淆
   public *;                                        
}
```
- <init>、<fields>、 <methods>的含义和使用
```
<init>;                //匹配所有的构造器
<fields>;              //匹配所有的域
<methods>;             //匹配所有的方法
//可以在以上的命令前加上public、private、native等来进一步指定不被混淆的内容
//也可以在以上的命令后面加上参数，来指定含有特定的参数构造方法或者方法名不会被混淆

-keep class pageName {
    public <init>;                                  //保留所有的public的构造方法不会被混淆
}

-keep class pageName {
    public <init>（java.lang.String）;              //保留所有的public的构造方法并且参数是String对象，不会被混淆
}

-keep class pageName {                              //保留所有的private的方法名不会被混淆
    private <methods>;
}
```

- 含有Keep关键字的含义（移除是指在压缩时(Shrinking)是否会被删除，需要开启压缩）
```
保留
防止被移除或者被重命名
防止被重命名

类和类成员
-keep
-keepnames

仅类成员
-keepclassmembers
-keepclassmembernames

如果拥有某成员，保留类和类成员
-keepclasseswithmembers
-keepclasseswithmembernames
```

