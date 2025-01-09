---
title: node版本引起的加密库OpenSSL无法支持算法问题
date: 2025-01-09 15:50:57
tags:
---

#### 问题描述

digital envelope routines::unsupported

#### 解决方法

在package.json文件中，将dev和build行修改为如下格式：

``` json
  "scripts": {
    "dev": "SET NODE_OPTIONS=--openssl-legacy-provider && vuepress dev src",
    "build": "SET NODE_OPTIONS=--openssl-legacy-provider && vuepress build src"
  },
```

#### 原因

这个错误是因为 Node.js 中的加密库 OpenSSL 版本过低，无法支持算法。您可以尝试使用 node@14 版本，或者在安装 Node.js 时选择包含较新的 OpenSSL 版本。如果您确实需要使用 Node.js v18.14.2 版本，可以更新 OpenSSL 版本来解决这个问题。具体的做法可以参考 OpenSSL 官方文档：https://www.openssl.org/docs/。