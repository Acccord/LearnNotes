## Android项目加入kotlin

### 第一步：项目build.gradle下添加
```
buildscript {
    ext.kotlin_version = '1.3.31'
    
    //...
    
    dependencies {
      //...
      classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}
```

### 第二步：module下build.gradle添加
```
apply plugin: 'kotlin-kapt'
apply plugin: 'kotlin-android'
apply plugin: 'kotlin-android-extensions'
android {
    //...
}
dependencies {
    //...
    implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:$kotlin_version"
}
```

### 其他情况
#### 1. 如果项目中有realm，那么module下build.gradle中「apply plugin: 'realm-android'」要放在kotlin下面
#### 2. 如果遇到com.android.dex.DexIndexOverflowException: method ID not in 65536错误。解决方案：
    在gradle文件中引入multidex
```
  android {
      //...
      defaultConfig {
          //...
          multiDexEnabled true
      }
      //...
  }
  dependencies {
      //...
      compile 'com.android.support:multidex:1.0.1'
  }
```
  在应用中开启这个方法,这里是在Applicaption中启动：
 ```
  @Override
  protected void attachBaseContext(Context base) {
      super.attachBaseContext(base);
      MultiDex.install(this);
  }   
 ```
