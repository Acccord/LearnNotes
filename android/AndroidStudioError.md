# AndroidStudio错误问题解决方案

### 1, ERROR: Unable to resolve dependency for xxx
> 问题描述：编译后出现上诉多行问题；产生原因：不清楚
  解决方案：
  - 1，Builder -> Clean Project
  - 2，切换下网络重新编译试试
  - 3，更新build.gradle重新编译试试
<br>

### 2. ERROR: No toolchains found in the NDK toolchains folder for ABI with prefix: mips64el-linux-android
> 原因：r17不再支持mips
  解决方案： 
  - 1，Gradle版本升级到高于3.0的版本,同时也需要将Android Studio升级到3.1或更高的版本.
  - 2，去[NDK官方下载](https://developer.android.google.cn/ndk/downloads/older_releases.html)17c或之前的版本，把项目toolchains中缺少的文件都copy进来。
<br>

### 3. Cause: error=2, No such file or directory/
报错详细：org.gradle.process.internal.ExecException: A problem occurred starting process 'command '/Users/vi/Library/Android/sdk/ndk-bundle/toolchains/mips64el-linux-android-4.9/prebuilt/darwin-x86_64/bin/mips64el-linux-android-strip''
	at org.gradle.process.internal.DefaultExecHandle.execExceptionFor(DefaultExecHandle.java:226)
	at org.gradle.process.internal.DefaultExecHandle.setEndStateInfo(DefaultExecHandle.java:204)
	at org.gradle.process.internal.DefaultExecHandle.failed(DefaultExecHandle.java:349)
	at org.gradle.process.internal.ExecHandleRunner.run(ExecHandleRunner.java:85)
	at org.gradle.internal.operations.BuildOperationIdentifierPreservingRunnable.run(BuildOperationIdentifierPreservingRunnable.java:39)
	at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:63)
	at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:46)
> 原因：原有的NDK由r16升级到r17，因为r17不再支持mips，导致上面文件找不到，删掉NDK或者降级使用r16的NDK，这其实是治标不治本的，解决办法是在build.gradle脚本里排除mips：
```
android {
    defaultConfig {
        ndk {
            //支持的CPU架构，如armeabi、x86、mips等
            abiFilters "armeabi", "x86"
        }
    }
    packagingOptions {
        doNotStrip '*/mips/*.so'
        doNotStrip '*/mips64/*.so'
    }
}
```

### 4. ERROR: SSL peer shut down incorrectly
> 原因：包下载不了
  解决方案： 
  - 1，切换下网络
