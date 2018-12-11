---
title:  React
tags:  React
notebook:  React
---
## React
<font color="red">React</font>  用于创建用户界面的JavaScript库

React 全家桶: 渐进式的 MVVM 框架

React 技术栈:
    React
    React-DOM
    React-router
    redux
    react-redux
    react-native
    antd
    脚手架

架构思想
    MVC  Model(数据模型) - view(视图) - control(控制器)
    MVVM Model(数据模型) - view(视图) - vm(view-Model 虚拟DOM)

### ReactDOM.render();
React.render(要渲染的内容，root);

### React.createElement()
通过 React.createElement() 创建一个 React 元素

reactElement React.createElement(tagName[,props,reactElement | children | inner])

参数：
    tagName： 小写的标签名称
    props：元素相关的属性
    reactElement：子元素
    children:一组子元素
    inner：内容

返回值：新生成的 reactElement

### JSX
jsx: react 的语法糖
javaScript + xml 在js中书写xml，或者说，给js添加xml的语法扩展

#### JSX 使用时注意事项：
- 可以在js中书写xml(html)
- 支持嵌套
- 一个独立的结构中，有且只能有一个顶级元素
- 支持{插值表达式} 在{}中我们可以使用js中的表达式
- 标签：小写 组件：首字母大写
- 所有标签都必须闭合

#### jsx 插值表达式
类似于 es6 中的模板字符串，可以在 xml 嵌入javascript 表达式
格式：{表达式}， 表达式：算数表达式，变量，函数调用

- 字符串，数字：原样输出
- 布尔值，空，未定义：输出空值，也不会有错误
- 对象：不能直接输出，但是可以通过其他方式，Object.values()等，去解析对象
- 数组：支持直接输出，默认情况下把数组通过空字符串进行拼接

#### jsx 属性操作
- 属性值加了引号，那么就是一个普通的属性书写方式
- 属性值也可以接受一个插值表达式
- class 要写作 className
- 在JSX中style的值只能是对象 `style={{property：value}}` 这个是{}中又嵌套了一个{}，外边的括号代表插值表达式，里面的括号是对象的括号

#### jsx 中的 循环 和 判断
- 插值表达式中不能写 if 和 for
- 如果需要判断可以使用 三目
- 如果需要使用循环 可以利用数组
- 复杂的逻辑 可以利用函数，函数的返回值就是要插入的数据

### 组件
组件可以将UI切分成一些独立的、可复用的部件，这样就只需专注于构建每一个单独的部件。

#### 类式组件
- class Name extends React.Component{} 类式组件要继承自 React.Component
- 组件的首字母必须大写
- 在组件内部有一个 render 方法 ，render 方法的返回值就是改组件要渲染的内容
- 组件调用: `<Name/>`

#### 函数式组件
- 函数式组件主要用于单纯的内容渲染
- 函数式组件只有props 没有state，并且没有生命周期
- 函数式组件要渲染的内容写在return里
- 尽量使用函数式组件保证程序性能更改

#### props 属性
- 设置属性，在调用组件时我们可以直接在组件上添加属性
- 在组件内容，我们可以调用 props 找到 加在组件上的属性
- 组件的props只读属性，不能在组件内部修改

#### 事件
- 注意事件是小驼峰 onClick={()=>{}}
- 在React中事件处理函数的this指向是undefined

#### state 状态
React 把组件看成是一个状态机(State Machines)。 通过与用户的交互，实现不同状态，然后渲染UI，让用户界面和数据保持一致。React里，只需要更新组件的state，然后根据新的state重新渲染用户界面(不需要操作 DOM)

- state 是组件的属性，本身就是一个对象，对象中存储了当前组件的各种状态
- 直接修改 state 不会重新渲染视图，调用setState 修改，会重新调用组件的render 方法
- 修改状态要调用setState({})方法，setState是异步操作
- 一个操作中多次调用setState，react会合并成一次执行

### 组件通信

#### 父组件向子组件传递消息
父级中，调用子组件时，把要传递的消息加给子组件做属性，然后子组件中，利用 props 接受 父级传递过来的消息

#### 子组件向父组件传递消息
在父级中，定义回调方法 传递给子级，子级再通过回调把消息传回

#### 兄弟组件传递消息
在父级中，定义回调方法，然后把回调方法传递给子级，子级再通过回调把消息传回，然后再传给另外一个组件

### 生命周期
- 挂载阶段(Mounting 初始化，实例过程)
   - constructor 构造函数
   - componentWillMount 即将挂载
   - render() 渲染
   - componentDidMount 已经挂载(放入真正的DOM)
- Updating: 正在被重新渲染(更新阶段)
   - 父组件更新，引起子组件更新          
      - componentWillReceiveProps(newporp)父组件的更新，引起子组件更新，在这可以拿到新的props
      - shouldComponentUpdate(newPorps,newState) 在组件接收到新的props或state时被调用
         返回值：true 更新继续执行，会重新渲染组件
                false 更新到此结束，组件不会重新渲染
      - componentWillUpdate(newPorps,newState) 组件即将更新
      - render();
      - componentDidUpdate(prevProps,prevState) 组件更新完毕

   - 组件本身更新
      - shouldComponentUpdate(newPorps,newState) 在组件接收到新的props或state时被调用
         返回值：true 更新继续执行，会重新渲染组件
                false 更新到此结束，组件不会重新渲染
      - componentWillUpdate(newPorps,newState) 组件即将更新
      - render();
      - componentDidUpdate(prevProps,prevState) 组件更新完毕
- Unmounting 卸载阶段
    componentWillUnmount 即将被卸载  

### 受控组件
- 可以通过初始state中设置表单的默认值;
- 每当表单的值发生变化时,调用onChange事件处理器;
- 事件处理器通过合成事件对象e拿到改变后的状态,并更新应用的state.
- setState触发视图的重新渲染,完成表单组件值得更新 

### key
- react中的key属性，它是一个特殊的属性，它是出现不是给开发者用的（例如你为一个组件设置key之后不能获取组件的这个key props），而是给react自己用的。
- react利用key来识别组件，它是一种身份标识标识，有了key属性后，就可以与组件建立了一种对应关系，react根据key来决定是销毁重新创建组件还是更新组件。
- key属性的使用场景最多的还是由数组动态创建的子组件的情况，需要为每个子组件添加唯一的key属性值。

### ref 
表示为对组件真正实例的引用，渲染组件时返回的是组件实例；而渲染dom元素时，返回是具体的dom节点。
eg：`<input ref = "input">` 可以通过this.refs.input可以获取到实例

### 路由
- 安装路由
  npm i react-router-dom -s 
- 使用
   - 选择要使用的路由
      - BrowserRouter
      - HashRouter
   - 用路由包含整个项目
   - Link组件 - 相当于 a 标签
      - to href跳转地址
   - route 识别路径显示不同的组件
      - path 要识别的路径
      - 默认情况： 只要url中包含了path，就显示
      - exact：严格匹配 url必须和path或path/ 一样才能显示出来
      - exact strict：更严格 url必须和 path完全一样
   - NavLink
       - 基本用法 和 Link 一致
       - activeClassName "class"
       - activeStyle = {{}}
       - isActive = {cb}
          - cb 返回值为 true 当前项选中
          - cb 返回值为 false 当前项不选中 
   - Switch
       当一项匹配成功之后，就不在执行下边的
  
### 脚手架 create-react-app
- 安装：npm i create-react-app -g
- 创建项目：create-react-app appName
- 启动：npm run start

### 配置 less
-  运行 npm run eject 把webpack配置显示出来
-  安装： 
    1）npm install less-loader less --save-dev
-  找到 config 下的 
    1）webpack.config.dev.js
    2）webpack.config-prod.js   
- 复制所有的 sass 配置 
- sass 修改成 less
