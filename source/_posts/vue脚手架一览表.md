---
title: vue脚手架一览表
date: 2025-01-06 16:01:29
categories:
- [Vue]
tags:
- [Vue]
---

##  vue脚手架一览表

1、使用 vue 脚手架安装项目
| 名称 | 描述 |
| --- | --- |
| node-v | 查看 node 版本 |
| npm -v | 查看 npm 版本 |
| nrm | 用来切换 npm 下载源：安装指令：npm install nrm -gnpm install nrm -g 可以使用 nrm ls，查看有哪些源 ;使用 nrm use XXX 切换下载源 |
| @vue/cli	| vue 较新版本的脚手架，用来创建 vue 项目：1、使用 npm install -g @vue/cli 安装脚手架 2、执行 vue create XXX，创建项目，项目名是 XXX 3、执行 cd XXX，进入项目 4、执行 npm run serve 启动项目。备注：如果之前安装过老版本的脚手架工具，可以使用 npm uninstall vue-cli -g 指令卸载一下 |


2、路由
| 名称 | 描述 |
| --- | --- |
| createRouter() | 创建路由 |
| path	| 配置路由路径 |
| name	| 配置路由的名字 |
| component	| 配置路由的组件 |
| router-link | 跳转路由的标签，具体跳到哪，可以用 to 属性来定义 |
| router-view | 负责展示当前路由对应的组件内容 |
| import |	异步加载路由 |

3、vuex
| 名称 | 描述 |
| --- | --- |
| createStore() | 创建 vuex，管理全局数据 |
| state	| 用来创建全局数据可以通过 this.$store.state.xxx 获取具体的数据 |
| actions |	定义 action |
| dispatch	| 派发 action |
| mutations	| 定义 mutations |
| commit	| 提交一个 commit，触发一个 mutation;在 action 中使用：this.commit(xxx);在 mutation 中使用：this.$store.commit(xxx) |
| modules	| 对 store 进行局部拆分（了解即可）|

4、发送 ajax 请求
| 名称 | 描述 |
| --- | --- |
| axios | 插件，用来发送 ajax 请求:npm install axios --save 通过 get 方法，发送 get 请求,通过 post 方法，发送 post 请求 |


5、插件  
| 名称 | 描述 |
| --- | --- |
| Vetur	| vscode 开发 vue 项目时，语法提示插件 |