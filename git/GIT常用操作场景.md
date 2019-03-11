## Git常用操作场景

### 1，拉取远程分支到本地（本地不存在的分支）
> git checkout -b 本地分支名 origin/远程分支名

这个将会自动创建一个新的本地分支，并与指定的远程分支关联起来。
<br>
<br>

### 2，首次提交本地分支到远程（远程不存在该分支） 
> git push origin dev:dev

这个将会自动创建一个新的远程分支，并关联起来。
<br>
<br>

### 3，从已有的分支(如master分支),创建一个创建新的分支（如dev分支）
> git checkout -b dev

这个将会创建一个新的分支并切换过去
<br>
<br>

### 4，删除远程分支
> git push origin --delete 远程分支名
<br>

### 5，删除本地分支
> git branch -d 本地分支名

删除本地分支时当前分支必须是其他分支
<br>
<br>

### 6，切换分支,保存临时修改
git切换到别的分支,要暂时保存当前分支的修改(不想进行add 和commit)的方法 
``` git
git stash
// git stash的话git stash的栈会直接给你一个hash值作为版本的说明

//or

git stash save “修改的信息"
// git stash save “修改的信息”，git stash的栈会把你填写的“修改的信息”作为版本的说明。
``` 

回到本分支后恢复代码
``` git
git stash pop
//git stash pop的作用是将git stash栈中最后一个版本取出来

//or

git stash list
git stash apply stash@{0}
//git stash apply stash@{0}的作用是可以指定栈中的一个版本，通过git stash list可以看到所有的版本信息：
```

### 7，手动添加忽略文件
``` git
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```

### 8，添加忽略单个文件
> git rm -r --cached <FILENAME>
<br>

### 9，切换远程仓库地址：
- 方式一：修改远程仓库地址
> git remote set-url origin URL //更换远程仓库地址，URL为新地址。
- 方式二：先删除远程仓库地址，然后再添加
> git remote rm origin //删除现有远程仓库

> git remote add origin [url] //添加新远程仓库
<br>

### 10、查看远程仓库的地址
> git remote -v
