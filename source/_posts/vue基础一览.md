---
title: vue基础一览
date: 2025-01-05 19:57:41
categories:
- [Vue]
tags:
- [Vue]
---

## Vue3基础一览表

Vue 是一套用于构建用户界面的渐进式框架

与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。 另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。

1、Vue 实例（应用）相关

| 名称      | 描述 |
| ----------- | ----------- |
| Vue.createApp()      | 创建 vue 实例（应用），参数可以决定根组件如何渲染       |
| mount(){}   | 该方法可以将 vue 实例，挂载在 dom 元素上        |
| template | 模板，用来定义该 vue 应用的展示内容。 |
| data(){}	| 用来定义数据 |
| ```{{}}``` | 插值表达式① 可以用来将变量渲染到 dom 结构中。用于起始标签与闭合标签之间② ```{{}}```中间可以写 js 表达式 |
| $data | vue 实例的属性，可以用来操作 data 中定义的数据 |
| methods:{} | 里面可以书写方法（函数） |
| computed:{} | 计算属性，当计算属性依赖的内容发生变更时，才会重新执行计算 |
| watch:{}	| 监听器，可以监听数据的改变，做异步操作 |


2、Vue 样式相关
| 名称      | 描述 |
| ----------- | ----------- |
|:class	| v-bind:class 的简写形式，为元素绑定动态类名 |
|$attrs	| 可以用来获取父组件绑定在子组件身上的属性（Non-Props 属性）|
|:style	| v-bind:style 的简写形式，为元素绑定动态的行内样式 |

3、Vue 常见指令
| 名称      | 描述 |
| ----------- | ----------- |
| v-on	| 绑定事件 ① “v-on:”可以简写成@ ② 可以使用“@[变量名]”，绑定动态事件。即，具体绑定哪个事件，由“变量名”决定 ③ 事件处理函数中，可以使用事件对象 event ④ 事件处理函数中，如果想传递多个参数，可以使用$event 指代事件对象 |
| v-if ，v-else-if ，v-else | 条件渲染：通过控制 dom 结构的存在与否来实现区块的显示和隐藏
三者可以组合使用 |
| v-show | 条件渲染：>通过控制元素的 display 属性来控制区块的显示和隐藏 |
| v-for | 列表渲染：用来循环数组、对象为了提高性能，可以使用 :key（前面没有出现:key,要不要考虑加上）为元素绑定唯一的 key 值 |
| v-model | ① 表单中的内容与 data 方法中的变量，进行双向数据绑定 ② 复选框，可以通过 true-value、false-value 属性指定选中、没选中时显示的值（不常用） ③ v-model 可以使用.lazy 修饰符，减少数据的变化频率（不常用） ④ v-model 可以使用.number 修饰符将数据转换成数字（不常用） ⑤ v-model 可以使用.trim 修饰符去除数据首尾的空格 |
| v-bind | ① 可以将标签/组件上的某个属性与数据变量进行绑定。 ② “v-bind:”可以简写成 “:” ③ 可以使用 “:[变量名]”，绑定动态属性。即，具体绑定哪个属性，由“变量名”决定 |
| v-html | 识别变量中的 html 标签；将变量中的 html 结构解析成 dom 结构 |
| v-once |	标签/组件只渲染一次；渲染一次后，如果数据变化，标签/组件的内容不会跟随变化 |

4、Vue 事件修饰符
| 名称      | 描述 |
| ----------- | ----------- |
| .prevent	| 阻止默认事件 |
| .stop	| 阻止事件冒泡 |
| .self	| 只有操作自身时，才会触发自身上的事件（常用于点击事件，即只有点击自己时，才会触发自身上绑定的点击事件） |
| .once	| 事件只触发一次 |
| .capture	| 把事件的运营模式变成捕获（不常用） |
| .passive	| 提升事件性能，常用于滚动事件 scroll（不常用） |

5、Vue 按键修饰符
| 名称      | 描述 |
| ----------- | ----------- |
| .enter | 触发事件的按键是 enter 键，才会真正触发事件。类似的按键修饰符还有.tab、.delete、.esc、.up、.down、.left、.right、.ctrl（不常用）|

6、鼠标修饰符
| 名称      | 描述 |
| ----------- | ----------- |
| .left | 触发事件的鼠标按键是左键，才会真正触发事件。类似的按键修饰符还有.right、.middle（不常用）|

7、精确修饰符
| 名称      | 描述 |
| ----------- | ----------- |
|.exact | 精确的按住指定键，才会触发事件（不常用）|

8、Vue dom 相关
| 名称      | 描述 |
| ----------- | ----------- |
| ref | 标签、组件设置该属性后，可以通过“this.$refs.xxx”的形式获取到该标签的 dom 节点、该组件的引用 |

9、创建组件
| 名称      | 描述 |
| ----------- | ----------- |
| app.component() | 组定义全局组件，其中“app”是保存 Vue 实例的变量 |
| components:{} | 注册局部组件 |

10、组件之间传值
| 名称      | 描述 |
| ----------- | ----------- |
| props | 父组件调用子组件时，可以通过标签属性的形式给子组件传值。子组件内部通过 props 属性接收传过来的值。子组件接收值时，可以进行校验：type 用来校验数据类型，default 用来设置默认值，require 用来设置必填 |
| Non-Props	| 父组件给子组件传递内容的时候，子组件不通过 props 接收。此时 vue 底层会把传递过来的属性，放在子组件最外层元素上，将其变成子组件的一个属性 |
| inheritAttrs | 用来设置子组件是否继承父组件传递过来的 Non-props 属性 |
| $emit | 子组件通过$emit 方法触发自定义事件，利用该事件可以给父组件传值 |
| emits | 声明组件会向外触发什么事件。通过 emits 属性我们就能知道该组件会向外触发什么事件 |
| v-model | 父子组件之间可以通过 v-model 实现双向数据绑定，子组件接收到的数据可以用modelValue 表示父组件要通过 v-model 给子组件绑定数据（选学绑定多个数据）|

11、动态组件
| 名称      | 描述 |
| ----------- | ----------- |
|  ``` <component/> ``` | 定义动态组件。具体显示哪个组件，由“:is”属性的值决定 |
| ``` <keep-alive></keep-alive>``` | 缓存标签。包裹动态组件后，可以保留上一个组件中的内容 |

12、异步组件
| 名称      | 描述 |
| ----------- | ----------- |
| Vue.defineAsyncComponent() |	该方法可以创建异步组件（了解即可） |

13、依赖、注入
| 名称      | 描述 |
| ----------- | ----------- |
| provide，inject | 祖先组件，通过 provide，可以向子孙组件注入依赖孙子组件，通过 inject，可以在可用的注入内容中搜索需要使用的内容，二者配合，可以实现祖先组件向子孙组件传值（一次性的） |


