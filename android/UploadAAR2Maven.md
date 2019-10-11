## 打包上传AAR文件到本地Maven仓库并且引用

### 打包AAR文件
  - [Android AAR开发打包方法、命名、依赖等相关注意点](https://www.jianshu.com/p/f47041fa1f5b)
  - [Android Studio 打包及引用 AAR](https://www.jianshu.com/p/1777a634db5e)
  
### 上传maven仓库

#### 上传本地maven仓库
  - [使用 Maven 管理 Android AAR](https://www.jianshu.com/p/0a7955459d71)
  
#### 上传本地和远程maven仓库
  - [Android 打包上传AAR文件到本地Maven仓库并且引用](https://blog.csdn.net/xiaxiayige/article/details/80636091)
上传远程maven仓库配置
``` gradle
  apply plugin: 'com.android.library'
  
  apply plugin: 'maven'
  
  
  android {
        
      defaultConfig {
          //...
      }
  
  
      buildTypes {
          release {
              //...
          }
          debug {
              //...
          }
      }
  }
  
  dependencies {
      //...
  }
  
  //发布maven配置
  uploadArchives {////新增 ，因为Android Studio gradle 支持maven插件，所以可以添加此task
      configuration = configurations.archives
      repositories {
          mavenDeployer {
              repository(url: 'http://xxxxx:xxxx/xxxxx/') {//maven仓库地址
                  authentication(userName: 'xxxxxx', password: 'xxxxxx')//配置用户名和密码
              }
              pom.project {
                  version '1.0.0' //版本号
                  artifactId 'xxx' 
                  groupId 'com.cn.vi'
                  packaging 'aar' //打包类型
                  description 'upload version 1.0.0' //说明
              }
          }
      }
  }
```
### 引用

  
