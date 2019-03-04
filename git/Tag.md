
## Tag

- git tag
// 查看tag，列出所有tag，列出的tag是按字母排序的，和创建时间没关系。
``` git
$ git tag
v0.1
v1.3
```

- git tag -l
//查看指定版本的tag，git tag -l “v1.4.2.**”
$ git tag -l 'v1.4.2.*'
v1.4.2.1
v1.4.2.2
v1.4.2.3
v1.4.2.4
1
2
3
4
5
6
git show
//显示制定tag的信息
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
1
2
3
4
5
6
7
8
9
10
11
12
13
14
git tag -a tagName -m “注释”
-m 后面带的就是注释信息，一般写当前的版本作用，这种是普通tag,-a 取 annotated 的首字母也可以给commit版本添加如下:git tag -a tagName   ef0264   -m "注释"
1
git push origin tagName
我们在执行 git push 的时候，tag是不会上传到服务器的，比如现在的github，创建 tag 后 git push ，在github网页上是看不到tag 的，为了共享这些tag，你必须这样：git push origin v1.0或者git push origin --tags
1
git push origin –tags
将所有tag 一次全部push到github上。
1
git tag -d tagName
删除tag
1
git push origin –detele tagName
删除github远端的指定tag
1
git checkout -b branchName tagName
    使用git checkout tag即可切换到指定tag，例如：git checkout v0.1.0
切换到tag历史记录会处在分离头指针状态，这个时候修改是很危险的，在切换回主线时如果没有合并，之前的修改提交基本都会丢失，如果需要修改可以尝试git checkout -b branch tag创建一个基于指定tag的分支，例如：git checkout -b tset v0.1.0  这个时候就会在分支上进行开发，之后可以切换到主线合并
--------------------- 
作者：Kenway090704 
来源：CSDN 
原文：https://blog.csdn.net/kenway090704/article/details/77854624 
版权声明：本文为博主原创文章，转载请附上博文链接！
