---
title: 将vite构建的vue3项目部署到githubpage教程
date: 2025-01-02 11:30:24
categories:
- [Vue]
tags:
- [Vue]
---

## 利用github page托管vue项目

1. 设置好vite.config.js

在 vite.config.js 中设置正确的 base。

如果你要部署在 ```https://<USERNAME>.github.io/ ```上，你可以省略 base 使其默认为 ```‘/’```。
如果你要部署在 ```https://<USERNAME>.github.io/<REPO>/``` 上，例如你的仓库地址为 ```https://github.com/<USERNAME>/<REPO>```，那么请设置 base 为 ```‘/<REPO>/’```。

2. 构建项目

``` bash
npm run build
# 或者
yarn build
```

执行上述命令后，就会看到根目录下，多了一个dist文件夹，这便是我们需要部署的文件夹。

3.预览项目

``` bash
npm run dev
```

4. 部署到github
如果上面的preview 没有问题，就可以部署到github了。

在github中，项目的源代码上传到了main分支，因此接下来要将dist 文件夹上传到另外一个分支，给这个分支起个名字gh-pages。

这里将dist 文件夹上传到gh-pages：(执行这条命令的前提是你已经完成了 git add. git commit git push 这些操作。)

``` bash
git subtree push --prefix dist origin(远程主机的名字) gh-pages
```

5. 开启pages功能
将分支切换到gh-pages，然后save，就能成功开启页面了！