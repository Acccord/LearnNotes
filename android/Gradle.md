# Gradle

## 异常情况
### bash: gradlew: command not found
mac下执行gradlew命令时，提示-bash ：gradlew command not found，主要原因是Android Project根目录下地gradlew文件没有执行权限。打开终端，执行以下命令：
> sudo chmod +x gradlew

为gradlew增加可执行权限。
值得一提的是，mac下执行当前目录下的命令需要在前面加上“./”，否则会到环境变量下找相应命令。例如
> ./gradlew javadocJar
