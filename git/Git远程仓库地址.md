## Git远程仓库地址

### 1、查看远程仓库的地址
> git remote -v

### 2、添加远程仓库的地址
> git remote add origin [url] //添加新远程仓库

### 3，切换远程仓库地址：
- 方式一：修改远程仓库地址
> git remote set-url origin URL //更换远程仓库地址，URL为新地址。
- 方式二：先删除远程仓库地址，然后再添加
> git remote rm origin //删除现有远程仓库
> git remote add origin [url] //添加新远程仓库


