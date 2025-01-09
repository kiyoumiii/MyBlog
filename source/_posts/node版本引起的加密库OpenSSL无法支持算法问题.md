---
title: node版本引起的加密库OpenSSL无法支持算法问题
date: 2025-01-09 15:50:57
tags:
---

#### 问题描述

digital envelope routines::unsupported

#### 解决方法

在package.json文件中，将serve和build行修改为如下格式：

``` json
  "scripts": {
   "serve": "SET NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service serve",
   "build": "SET NODE_OPTIONS=--openssl-legacy-provider && vue-cli-service build"
},
```

#### 原因

这个错误是因为 Node.js 中的加密库 OpenSSL 版本过低，无法支持算法。
因为 node.js V17版本中最近发布的OpenSSL3.0, 而OpenSSL3.0对允许算法和密钥大小增加了严格的限制，可能会对生态系统造成一些影响。故此以前的项目在升级 nodejs 版本后会报错。

您可以尝试使用 node@14 版本，或者在安装 Node.js 时选择包含较新的 OpenSSL 版本。如果您确实需要使用 Node.js v18.14.2 版本，可以更新 OpenSSL 版本来解决这个问题。具体的做法可以参考 OpenSSL 官方文档：https://www.openssl.org/docs/。