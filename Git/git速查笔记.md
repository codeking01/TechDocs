## 如何删除暂存区的文件(从暂存区变成未追踪，即取消文件追踪)

```git
git rm -rf --cached .
git rm -rf --cached xx-file
git rm -rf --cached xx-fold/
```



### 删除未追踪的文件或者文件夹

    git clean -fd xx-fold/
    # 文件
    git clean -fd xx-file



## 允许大文件推送

```git
git lfs install
git config lfs.contenttype false # 禁用内容类型设置，这就可以推送了
```



### 支持长文件名

```git
git config --global core.longpaths true
```



### 回退某一个文件或者文件夹到指定提交

法一：checkout

```git
git checkout <commit-hash> -- xx-fold/
# 文件
git checkout <commit-hash> -- xx-file
```

法二：

```git
git restore --source=<commit-hash> -- xx-fold/
git restore --source=<commit-hash> -- xx-file
```



## 修改提交文件（包括新增，删除）

操作语句`amend-x`

```git
git commit --amend
```

退出后可以查看修改文件数量等信息。

1. 新增
   新增文件
   执行`git add new-file`
   执行`amend-x`语句，然后`:wq`退出即可

2. 修改
   修改文件
   执行`git add modified-file`
   执行`amend-x`语句，然后`:wq`退出即可

3. 取消旧文件提交
   取消文件追踪：`git rm -rf --cached deleted-file`
   执行`amend-x`语句，然后`:wq`退出即可
   
   

## 强制切换到某一远程分支

```git
git checkout origin/xx-branch -f
```



## 强制重置到某一远程分支

```git
git reset origin/xx-branch --hard
```

## 推送大文件

```
git lfs install
```

```
使用以下命令指定要用 LFS 跟踪的文件类型。 示例：跟踪所有 PSD 文件
git lfs track "*.psd" 
# 或者指定文件
git lfs track xx.txt

# 然后会出现下面 .gitattributes文件，内容如下
xx.txt filter=lfs diff=lfs merge=lfs -text
```

```
# 记得将 .gitattributes 文件添加到版本控制中，然后像平常一样提交：
git add .gitattributes
```


