---
title:  vue
tags:  vue
notebook: vue
---
# VUE 
VUE是一套用于构建用户界面的渐进式框架

VUE的两大核心:数据驱动和组件系统

## VUE 生命周期
VUE的生命周期,就是vue实例从创建到销毁的过程，从创建实例，到初始化数据，编译模板，挂载DOM，渲染DOM，到更新DOM，渲染DOM，销毁等一系列过程，称之为vue的生命周期

VUE生命周期的作用：VUE生命周期中有很多事件钩子，可以让我们在控制整个VUE实例中更能形成好的逻辑

VUE生命周期总共有8个阶段：创建前后(beforeCreate，created)，挂载前后(beforeMounte，mounted)，更新前后(beforeUpdate，updated)，销毁前后(beforeDestroy，destroyed)， 第一次加载页面时会触发钩子函数beforeCreate，created，beforeMounte，mounted，DOM渲染是在mounted中就已经完成了

## VUE实现数据双向绑定的原理 Object.defineProperty（）
VUE实现数据双向绑定主要是：采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的getter和setter，在数据发生变动时发布消息给订阅者，触发相应的监听回调.当把一个普通 Javascript 对象传给 Vue 实例来作为它的 data 选项时，Vue 将遍历它的属性,用 Object.defineProperty() 将它们转为 getter/setter。用户看不到 getter/setter，但是在内部它们让 Vue 追踪依赖，在属性被访问和修改时通知变化

## VUE路由的实现 hash和history
hash模式：在浏览器地址栏中符号“#”以及“#”后面的字符统称为hash，特点：hash虽然在url中，但不被包括在HTTP请求中；因此对后端来说，即使没有做到对路由的全覆盖，也不会返回404错误，hash不会重载页面

history模式：history采用了HTML5新特性，history模式下，前端的url必须和实际向后端发起的url一致，如果后端缺少处理则会返回404错误

## VUEX
VUEX，集中的状态管理，只是用来读取的状态集中放在store中；改变状态的方法是提交mutations，这是同步的事物，异步逻辑应该封装在action中

state

Vuex 使用单一状态树,即每个应用将仅仅包含一个store 实例，但单一状态树和模块化并不冲突。存放的数据状态，不可以直接修改里面的数据。

mutations

mutations定义的方法动态修改Vuex 的 store 中的状态或数据。

getters

类似vue的计算属性，主要用来过滤一些数据。

action 

actions可以理解为通过将mutations里面处里数据的方法变成可异步的处理数据的方法，简单的说就是异步操作数据。view 层通过 store.dispath 来分发 action。

modules

项目特别复杂的时候，可以让每一个模块拥有自己的state、mutation、action、getters,使得结构非常清晰，方便管理。

父子组件之间传值

父组件传给子组件：子组件通过props方法接受数据;子组件传给父组件：$emit方法传递参数；也可以用vuex


## VUE $route和$router的区别
$route是“路由信息对象”，包括path，params，hash，query，fullPath，matched，name等路由信息参数。而$router是“路由实例”对象包括了路由的跳转方法，钩子函数等。

## VUE 计算属性
在模板中放入太多的逻辑会让模板过重且难以维护，在需要对数据进行复杂处理且可能多次使用的情况下，尽量采用计算属性的方式。好处：1，使得数据处理结构清晰；2，依赖于数据，数据更新，处理结果自动更新；3，计算属性内部this指向vm实例； 4，常用的是getter方法，获取数据，也可以使用set方法改变数据； 5，相比较于methods，不管依赖的数据变不变，methods都会重新计算，但是依赖数据不变的时候，computed从缓存中获取，不会重新计算 ，watch更类似于一个回调函数

## VUE keep-alive
keep-alive是vue的一个内置组件，可以使被包含的组件保留状态，或避免重新渲染 

keep-alive的两个属性include(包含的组件缓存)与exclude(排除的组件不缓存，优先级大于include)

参数解释

include - 字符串或正则表达式，只有名称匹配的组件会被缓存

exclude - 字符串或正则表达式，任何名称匹配的组件都不会被缓存

include 和 exclude 的属性允许组件有条件地缓存。二者都可以用“，”分隔字符串、正则表达式、数组。当使用正则或者是数组时，要记得使用v-bind 。

## VUE知识点总结
- css只在当前组件起作用：在style标签中写入scoped即可
- v-if 和 v-show的区别：v-if按照条件是否渲染，v-show是display的block或none
- vue几种常用的指令 v-for 、 v-if 、v-bind、v-on、v-show、v-else，v-model
- vue中key值的作用 为了高效的更新虚拟DOM
- vue中的组件是可以共享的，但是data是私有的，所以每个组件都必须return一个新的data对象，返回一个唯一的对象，这都是js本身的特性带来的，跟vue本身设计无关
- v-for 和 v-if的优先级：当它们处于同一节点，v-for的优先级比v-if更高，这就意味着v-if将分别重复运行于每个v-for循环中
- vue更新数组时触发视图更新的方法：push，pop，shift，unshift，splice，sort，reverse
- 由于javascript限制，vue不能检测到以下变动
   - 利用索引直接设置一个数组项无效
   - 修改数组长度无效
   - vue也不能检测到对象属性的添加和删除
- 