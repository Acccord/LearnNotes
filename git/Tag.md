
## Tag
## 常用命令
- 打印所有标签
``` git
    // 查看所有tag，按字母排序的，和创建时间没关系。
    git tag
```

- 打印符合检索条件的标签
``` git
    //查看指定版本的tag，git tag -l <版本号>
    git tag -l 'v1.4.2.*'
```

- 显示制定tag的信息
``` git
    //git show <版本号>
    $ git show v1.4
    tag v1.4
    Tagger: Scott Chacon <schacon@gee-mail.com>
    Date:   Mon Feb 9 14:45:11 2009 -0800

    my version 1.4

    commit 15027957951b64cf874c3557a0f3547bd83b3ff6
    Merge: 4a447f7... a6b4c97...
    Author: Scott Chacon <schacon@gee-mail.com>
    Date:   Sun Feb 8 19:02:46 2009 -0800

    Merge branch 'experiment'
``` 

- 创建本地标签
``` git
    //创建轻量标签
    //指向一个发行版的分支，其只是一个像某commit的引用，不存储名称时间戳及标签说明等信息。定义方法如下
    git tag <版本号>-light
    
    //创建带附注标签
    //相对于轻量标签，附注标签是一个独立的标签对象，包含了名称时间戳以及标签备注等信息，同时指向对应的commit
    git tag -a <版本号> -m "<备注信息>"
    
    //创建带附注标签
    //同时我们也可以像特定的commit添加标签，使用该commit对应的SHA值即可
    git tag -a <版本号> <SHA值> -m "<备注信息>"
    //比如 git tag -a 1.0.0 0c3b62d -m "Release Edition v1.0.0" 就是为SHA为0c3b62d的这次提交打了1.0发行版的tag
```

- 删除本地标签
``` git
    git tag -d <版本号>
```

- 将本地标签提交到远程仓库
git push origin tagName
``` git
    我们在执行 git push 的时候，tag是不会上传到服务器的
    比如现在的github，创建 tag 后 git push ，在github网页上是看不到tag 的
    为了共享这些tag，你必须这样：git push origin v1.0或者git push origin --tags
    
    //推送所有标签
    git push origin --tags
    
    //推送指定版本的标签
    git push origin <版本号>
    
```

- 删除远程仓库的标签

``` git
    //git push origin –detele <版本号>
    git push origin –detele tagName
``` 

- 切换到指定标签
``` git
    使用git checkout tag即可切换到指定tag，例如：git checkout v0.1.0
    切换到tag历史记录会处在分离头指针状态，这个时候修改是很危险的，在切换回主线时如果没有合并，之前的修改提交基本都会丢失
    如果需要修改可以尝试git checkout -b branch tag创建一个基于指定tag的分支
    例如：git checkout -b tset v0.1.0  这个时候就会在分支上进行开发，之后可以切换到主线合并
```

## 场景操作
- 删除 GitHub 上某个 tag/release
``` git
git tag -d [tag];
git push origin :[tag]
``` 

假若需要删除一个 v1.1.1 的 release 版本
``` git
git tag -d v1.1.1;
git push origin :v1.1.1
```

- 常用命令
```
    // 查看标签
    // 打印所有标签
    git tag
    // 打印符合检索条件的标签
    git tag -l 1.*.*
    // 查看对应标签状态
    git checkout 1.0.0

    /// 创建标签(本地)
    // 创建轻量标签
    git tag 1.0.0-light
    // 创建带备注标签(推荐)
    git tag -a 1.0.0 -m "这是备注信息"
    // 针对特定commit版本SHA创建标签
    git tag -a 1.0.0 0c3b62d -m "这是备注信息"

    /// 删除标签(本地)
    git tag -d 1.0.0

    /// 将本地标签发布到远程仓库
    // 发送所有
    git push origin --tags
    // 指定版本发送
    git push origin 1.0.0

    /// 删除远程仓库对应标签
    // Git版本 > V1.7.0
    git push origin --delete 1.0.0
    // 旧版本Git
    git push origin :refs/tags/1.0.0
```
