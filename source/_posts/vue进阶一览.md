---
title: vue进阶一览
date: 2025-01-05 21:07:22
categories:
- [Vue]
tags:
- [Vue]
---

## Vue3进阶一览表

1、Vue 的设计模式

| 名称      | 描述 |
| ----------- | ----------- |
| mvvm | m 代表 model，指代数据；v 代表 view，指代视图；vm 代表 viewModel，指代视图数据连接层 |
| vm | 自定义的变量名，用来接收 app.mount()的返回值，代表 vue 应用的根组件。利用该变量，可以使用 vm.$data 直接访问、操作根组件上的数据 |

2、Vue 生命周期函数

| 名称      | 描述 |
| ----------- | ----------- |
| beforeCreate() | 在实例生成之前，会自动执行该函数 |
| created() | 在实例生成之后，会自动执行该函数 |
| beforeMount() | 在组件内容被渲染到页面之前，会自动执行该函数 |
| mounted() | 组件内容被渲染到页面后，会自动执行该函数 |
| beforeUpdate() | 当 data 中的数据发生变化时会自动执行该函数 |
| updated() | 当 data 中的数据发生变化，同时页面完成更新后，会自动执行的函数 |
| beforeUnmount() | 当 Vue 应用失效时，会自动执行该函数 |
| unmounted() | 当 Vue 应用失效后，同时 dom 完全销毁之后，自动执行的函数 |

3、vue 实例的方法
| 名称      | 描述 |
| ----------- | ----------- |
| unmount()	| 销毁 vue 应用 |

4、插槽
| 名称      | 描述 |
| ----------- | ----------- |
| ```<slot></slot>``` | 插槽。父组件可以利用插槽往子组件中传入 dom 结构 |
| name | 定义插槽的名字(具名插槽）。父组件要使用“v-slot:插槽名”指定为哪个插槽传递内容“v-slot:插槽名”可以简写成“#插槽名” |
| ``` <template></template> ``` | 占位符 |
| v-slot |	父组件利用 v-slot 可以接收到子组件绑定到插槽上的数据 |

5、标签、组件的过渡与动画
| 名称      | 描述 |
| ----------- | ----------- |
| ```<transition></transition>``` |	用来给标签、组件添加过渡效果 |
| .v-enter-from | 元素准备入场时的默认类名 |
| .v-enter-to | 元素准备离场时的默认类名 |
| .v-enter-active | 元素入场时的默认类名 |
| .v-leave-from | 元素准备离场时的默认类名 |
| .v-leave-to | 元素已经离场后的默认类名 |
| .v-leave-active | 元素离场过程中的默认类名 |
| name | 通过给<transition></transition>组件设置 name 属性，可以统一修改元素做动画时的类名 |
| .enter-from-class | 单独设置元素准备入场时的类名 |
| .enter-active-class | 单独设置元素入场的过程中的类名 |
| .enter-to-class | 单独设置元素入场之后的类名 |
| .leave-from-class | 单独设置元素准备出场时的类名 |
| .leave-active-class | 单独设置元素出场过程中的类名 |
| .leave-to-class | 单独设置元素出场之后的类名 |
| type | 当元素既有过渡又有动画，并且二者时间不一致时，使用 type 属性，可以指定以哪一个时间为准 |
| :duration | 设置过渡、动画的时间，单位是毫秒 |
| :css | 设置是否使用 css 动画 |
| @before-enter | 元素准备入场时的钩子 |
| @enter | 元素入场过程中的钩子 |
| @after-enter | 元素入场结束时的钩子 |
| @before-leave | 元素准备出场时的钩子 |
| @leave | 元素出场过程中的钩子 |
| @leave-after | 元素出场结束时的钩子 |
| mode | 设置多个单元素之间状态切换时，可以采取的模式：out-in：先隐藏，再进来 in-out：先进来，再隐藏 |
| appear | 设置初次显示的元素，也有动画效果 |

6、列表动画
| 名称      | 描述 |
| ----------- | ----------- |
| ``` <transition-group></transition-group> ``` | 用来定义列表动画。使用该组件包裹的一组元素，当元素新增或减少时，可以设置动画效果。动画的相关效果可以设置在默认类名 v-enter-from、v-enter-active、v-enter-to、v-leave-from、v-leave-active、v-leave-to 下 |
| .v-move	| 列表元素移动过程中的，默认的类名 |

7、 mixin 混入
| 名称      | 描述 |
| ----------- | ----------- |
| mixins | 定义局部的混入 |
| app.mixin() | 定义全局的混入 |
| $options | 可以通过该属性，获取 vue 应用中的自定义属性 |
| app.config.optionMergeStragies |	为自定义选项定义合并策略 |

8、自定义指令 directive
| 名称      | 描述 |
| ----------- | ----------- |
| app.directive() |	定义全局自定义指令，使用指令时，直接在元素上写上“v-指令名”即可，自定义指令时，也可以使用 mounted、updated 等生命周期函数 |
| directives:{} | 引入局部指令 |
| binding |	获取指令上的相关信息 |

9、teleport 传送门 
| 名称      | 描述 |
| ----------- | ----------- |
| ```<teleport></teleport>``` |	传送门，用来将包裹的内容，传送到 to 属性对应的 dom 元素下 | 

10、 render 函数（选学）
| 名称      | 描述 |
| ----------- | ----------- |
| render() |	用来定义组件的内容 |
| $slots |	用来获取插槽的相关内容 |

11、 plugin 插件
| 名称      | 描述 |
| ----------- | ----------- |
| install(){} |	定义插件时，会执行的方法 |
| app.use() | 使用插件 |
| app.provide()	| 注入全局依赖 |
| app.config.globalProperties | 扩展全局属性 |
| $watch |	vue 实例的方法，用来监听数据 |

12、 composition API
| 名称      | 描述 |
| ----------- | ----------- |
| setup(){} |	实例被完全初始化之前执行的函数，可以使用 this.$options.setup()获取 setup 函数中的返回值 |
| ref() |	将基础类型的数据，转成响应式 配合 ref 属性，可用于获取 dom 节点 |
| reactive() |	将非基础型的数据，转成响应式 |
| readonly() |	将响应式数据转成只读数据 |
| toRefs()	| 从响应式对象中解构出具备响应式的数据 |
| toRef() | 可以从响应式数据中解构出不存在的数据，并且解构出来的值是响应式的 |
| context |	setup 函数的第二个参数，可以用来获取到 None-Props 属性、插槽，以及 emit 方法 |
| computed() |	用来定义计算属性，里面可以写 get、set 方法 |
| watch() |	监听器，可以让其监一个或多个数据的变化 |
| immediate	| 配置 watch 监听器，让其变成非惰性 |
| watchEffect() |	监听器，会自动检测自己内部的代码，如果自己内部代码的某些依赖变化了，watchEffect 方法就会自动执行 |
| provide()	| 祖先组件，通过 provide，向子孙组件注入依赖 |
| inject() | 子孙组件，通过 inject，来获取祖先组件注入的依赖 |
| useStore() | 用来获取 store，从而操作 vuex 中的数据 |


13、composition API 中的生命周期函数
| 名称      | 描述 |
| ----------- | ----------- |
| onBeforeMount(){} |	vue 实例即将挂载到页面上的时候执行，等价于 beforeMount |
| onMounted(){} |	vue 实例挂载到页面上之后执行，等价于 mounted |
| onBeforeUpdate(){} |	当数据发生变化时执行，等价于 beforeUpdate |
| onUpdated(){} |	当数据发生变化，同时页面完成更新后，会自动执行，等价于 updated |
| onBeforeUnmount(){} |	组件从页面移除之前，会自动执行该函数，等价于 beforeUnMount |
| onUnmounted(){} |	组件从页面移除之后，自动执行的函数，等价于 unmounted |
| onRenderTracked(){} | 每次渲染之后，收集依赖的时候会自动执行的函数 |
| onRenderTriggered(){}	| 每次重新渲染被触发的时候，自动执行的函数 |


