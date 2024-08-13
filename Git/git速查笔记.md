## 如何删除暂存区的文件

```git
git rm -rf --cached .
```



## 允许大文件推送

```git
git lfs install
git config lfs.contenttype false # 禁用内容类型设置，这就可以推送了
```



### 支持长文件名

```git
git config --global core.longpaths true
```
