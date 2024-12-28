---
title: 超级常用的一些git命令
date: 2024-12-28 18:32:09
categories:
- [计算机科学]
tags:
- [git]
---

常用git命令一览表

<br>
<div align="center">
    <img src="超级常用的一些git命令/01.jpg">
</div>
<br>

自用的一些常备git命令：

``` bash
# 重命名分支
git branch -m <old_name> <new_name>
```

``` bash
# 查看分支
git branch
```

``` bash
# 切换分支
git checkout <branch_name>
```

``` bash
# 拉取分支
git pull origin <branch_name>
```

``` bash
# 推送分支
git push origin <branch_name>
```

``` bash
# 查看提交记录
git log
```
``` bash
# 合并分支
git merge <branch_name>
```

``` bash
# 强制覆盖
git reset --hard <commit_id>
```

``` bash
# 回退版本
git reset --soft <commit_id>
```

``` bash
# 把本地分支kiyoumi推送到远程分支develop
git push origin kiyoumi:develop
```

``` bash
# 把远程分支develop拉取到本地分支kiyoumi
git pull origin develop:kiyoumi
```

```bash
# 从远程分支把该文件直接替换
git checkout origin/remote -- <file_path>
```


