---
title: vue3-Router路由
date: 2024-09-17 19:44:44
categories:
- [Vue]
tags:
- [Vue]
---

# router-view标签

### 场景：
原本在edit页面，通过v-if绑定侧边栏，当点击侧边栏内的按钮后，URL会发生改变，携带tempID返回构成一个新的URL。需求是URL发生变化后页面重新跳转至新的URL页面，实际是页面并没有刷新，即使URL栏已经改变，需要手动刷新后才能到预期的URL页面

### 问题解决思路:

你可以把router-view当做是一个容器，它渲染的组件是你使用vue-router指定的

``` html
<template>
  <section class="app-main">
    <transition name="fade-transform" mode="out-in">
      <router-view :key="key" /> //key属性
    </transition>
  </section>
</template>

<script>
export default {
  name: 'AppMain',
  computed: {
    key() {
      return this.$route.fullPath
    }
  }
}
</script>

```

这里router-view有一个key的属性，这个key的属性作用是：

### 1. 不设置router-view的key属性

由于Vue会复用相同组件，即/page/a => /page/b或者/page?id=a => /page?id=b这类链接跳转时，将不再执行created，mounted之类的钩子，这时候你需要在路由组件中，添加beforeRouteUpdate钩子来执行相关方法拉取数据

### 2. 设置router-view的key属性值为$route.path

从/page/a => /page/b，由于这两个路由的$route.path并不一样，所以组件被强制不复用，相关钩子加载顺序为beforeRouteUpdate => created => mounted

从/page?id=a => /page?id=b，由于这两个路由的$route.path一样，所以和没设置key属性一样，会复用组件，相关钩子加载顺序为：beforeRouteUpdate

### 3. 设置router-view的key属性值为$route.fullPath

从/page/a => /page/a，由于这两个路由的$route.fullPath并不一样，所以组件被强制不复用，相关钩子加载顺序为`beforeRouteUpdate => created => mounted`

从/page?id=a => /page?id=b，由于这两个路由的$route.fullPath并不一样，所以组件被强制不复用，相关钩子加载顺序为`beforeRouteUpdate => created => mounted`

### 最终解决方案：
在App.vue中加入上述代码片段，设置router-view的key属性值为$route.fullPath，这样一来，新的ID返回后组件强制不复用，就可以实现页面重新加载跳转的效果。
