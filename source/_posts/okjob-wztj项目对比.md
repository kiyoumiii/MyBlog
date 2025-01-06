---
title: okjob-wztj项目对比
date: 2025-01-05 19:53:36
categories:
- [Vue]
tags:
- [前端开发]
---

## 项目总结与对比

### OK-JOB

VueX

watch

事件修饰符.prevent

props选项

$emit和v-on（@）

Props + emit

Vue-cli项目（npm run serve启动，8080监听）

lang = javascipt

lang = scss

mixins混入


### 王者图鉴

pinia

动态组件：```<component>+: is```实现

watchEffect

defineProps宏

defineEmits宏

defineModel宏

Vite4项目（npm run dev启动，5173监听）

slot插槽

lang = typescript

lang = less

通过依赖注入（provide+inject）解决vue多层组件逐级透传问题


### 注解

1. Vuex 和 Pinia 都是 Vue.js 的状态管理库，用于帮助开发者管理大型应用中的全局状态。它们的主要功能是提供一个集中存储和管理应用状态的机制，使得状态的更新和访问更加可预测和可维护。
** API风格 **
Pinia使用类似Vue组件的API来创建和使用store，而Vuex使用一个全局对象来访问store。
在Pinia中，状态是响应式的，这意味着当状态发生变化时，组件会自动更新。在Vuex中，我们需要手动触发更新。
Pinia的store是模块化的，这意味着每个store可以包含自己的状态、操作和插件。在Vuex中，store是全局的，这意味着所有的状态和操作都在同一个store中。
** Vuex 的功能 **
- 集中存储状态：Vuex 提供了一个全局的 state 对象，所有组件都可以访问和修改这个状态。
- 严格的状态更新规则：状态只能通过提交 mutation 来更新，而 mutation 必须是同步的。
- 异步操作：通过 actions 来处理异步逻辑，然后提交 mutation 更新状态。
- 模块化：支持将状态管理拆分成多个模块，每个模块可以有自己的 state、getters、mutations 和 actions。
- 严格模式：可以开启严格模式来确保状态只通过 mutation 来更新，避免状态被意外修改。

``` javascript
// store.js
import Vuex from 'vuex'

export default new Vuex.Store({
  state: {
    count: 0,
  },
  mutations: {
    increment(state) {
      state.count++
    },
    decrement(state) {
      state.count--
    },
  },
  actions: {
    increment({ commit }) {
      commit('increment')
    },
    decrement({ commit }) {
      commit('decrement')
    },
  },
})

// 组件中使用
import { mapState, mapActions } from 'vuex'

export default {
  computed: mapState({
    count: state => state.count,
  }),
  methods: mapActions(['increment', 'decrement']),
}


```

** Pinia 的功能 **
- 更简洁的 API：Pinia 提供了更简洁和直观的 API，使得状态管理更加简单易用。
- 组合式 API 支持：Pinia 完全基于 Vue 3 的组合式 API 设计，与 Vue 3 的特性（如 setup 函数）更加契合。
- 无严格模式：Pinia 不需要严格模式，因为它的设计使得状态更新更加自然和安全。
- 类型推断：Pinia 提供了更好的 TypeScript 支持，能够自动推断状态的类型，减少了类型注解的需要。
- 插件系统：支持插件系统，可以扩展 Pinia 的功能。

``` javascript
import { defineStore } from 'pinia'

export const useCounterStore = defineStore({
  id: 'counter',
  state: () => ({
    count: 0,
  }),
  actions: {
    increment() {
      this.count++
    },
    decrement() {
      this.count--
    },
  },
})

```

** 区别 **
- API 设计：Vuex 的 API 相对复杂，需要定义 state、getters、mutations、actions 等多个部分，而 Pinia 的 API 更为简洁，通过 defineStore 函数来定义状态管理。
- 与 Vue 的集成：Vuex 主要与 Vue 2 和 Vue 3 的选项式 API 集成，而 Pinia 完全基于 Vue 3 的组合式 API 设计，更适合 Vue 3 的开发方式。
- 类型支持：Pinia 提供了更好的 TypeScript 支持，能够自动推断类型，而 Vuex 在 TypeScript 支持方面需要更多的类型注解。
- 性能和易用性：Pinia 由于其简洁的设计和与 Vue 3 的紧密集成，通常被认为在性能和易用性上更优。
- 社区和生态：Vuex 是 Vue.js 的官方状态管理库，拥有较大的社区和丰富的生态支持，而 Pinia 是 Vue 3 推荐的状态管理库，逐渐在社区中获得更多的关注和支持。

2. watch 和 watchEffect 是 Vue 3 中用于响应式地观察数据变化的两个 API，它们在使用场景和行为上有一些区别。
** watch **
watch API 与vue2选项式 API this.$watch (以及相应的 watch 选项) 完全等效。watch
需要侦听特定的数据源，并在单独的回调函数中执行副作用。默认情况下，它也是惰性的——即回调仅在侦听源发生变化时被调用。

``` javascript
// 侦听一个 getter
const state = reactive({ count: 0 })
watch(
  () => state.count,
  (count, prevCount) => {
    /* ... */
  }
)

// 直接侦听一个 ref
const count = ref(0)
watch(count, (count, prevCount) => {
  /* ... */
})

//监听多个源
watch([fooRef, barRef], ([foo, bar], [prevFoo, prevBar]) => {
  /* ... */
})
```

** watchEffect **
立即执行传入的一个函数，同时响应式追踪其依赖，并在其依赖变更时重新运行该函数。

``` javascript
const count = ref(0)

watchEffect(() => console.log(count.value))
// -> logs 0

setTimeout(() => {
  count.value++
  // -> logs 1
}, 100)

```

区别
- 执行时机：watchEffect是立即执行的，在页面加载时会主动执行一次，来收集依赖；而watch是惰性地执行副作用，它不会立即执行，但可以配置 immediate，使其主动触发
- 参数不同：watchEffect只需要传递一个回调函数，不需要传递侦听的数据，它会在页面加载时主动执行一次，来收集依赖；而watch至少要有两个参数（第三个参数是配置项），第一个参数是侦听的数据，第二个参数是回调函数
- 结果不同：watchEffect获取不到更改前的值；而watch可以同时获取更改前和更改后的值


3. 语法糖内的defineProps及defineEmits、defineExpose

defineProps 和 defineEmits 都是只能在 <script setup> 中使用的编译器宏。他们不需要导入，且会随着 <script setup> 的处理过程一同被编译掉。

defineProps 接收与 props 选项相同的值，defineEmits 接收与 emits 选项相同的值，它们具备完整的类型推断并且在 script setup 中是直接可用的。

defineProps 或 defineEmits 要么使用运行时声明，要么使用类型声明。同时使用两种声明方式会导致编译报错

- defineProps
获取组件传值: 父传子 defineProps

``` javascript
<template>
  <h1>{{ msg }}</h1>
  <div @click="clickThis">1111</div>
</template>

<script setup lang="ts">
  defineProps<{ // 采用ts专有声明，无默认值
    msg: string,
    num?: number
  }>()
     // 采用ts专有声明，有默认值
    interface Props {
        msg?: string
        labels?: string[]
    }
    const props = withDefaults(defineProps<Props>(), {
        msg: 'hello',
        labels: () => ['one', 'two']
    })
    
  defineProps({ // 非ts专有声明
    msg: String,
    num: {
      type:Number,
      default: ''
    }
  })
</script>

<style scoped lang="less">
</style>

```

- defineEmits
defineEmits 子组件向父组件事件传递:子传父
``` javascript
<template>
  <div @click="clickThis">点我</div>
</template>

<script setup lang="ts">
    /*ts专有*/
  const emit= defineEmits<{
    (e: 'click', num: number): void
  }>()
    /*非ts专有*/
  const emit= defineEmits(['click'])
  
  const clickThis = () => {
    emit('click',2)
  }
</script>

<style scoped lang="less">
</style>

```

- defineExpose
子组件暴露属性和方法给父组件 defineExpose

``` javascript
<template>
  <div>子组件helloword.vue</div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const count = ref(123456)
defineExpose({
  count
})
</script>

<style scoped lang="less">
</style>
```









