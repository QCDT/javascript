---
title:  Redux
tags:  Redux
notebook:  Redux
---
## redux 
Redux是 javaScript 状态容器，提供可预测化的状态管理

### 为什么要使用 Redux
可以构建一致化应用，运行于不同的环境(客户端，服务器，原生应用)， 并且易于测试

### 安装 Redux 
yarn add redux / npm i redux

### Redux 使用

#### createStore(reducer,[preloadedState],[enhancer])
- 返回值： store仓库，存储数据状态
   - dispatch(action)发起一个动作
   - getState()获取状态
   - subscribe(listen) 监听器： 每当有新的动作，监听器就会调用listen函数
- reducer 纯函数
   1) 状态的操作和管理
   2) reducer 必须偶一个返回值，返回值就是操作过后，新的state
   - state 状态
   - action 动作(操作)
      1) 默认必须一个对象
      2) 对象必须有一个type属性
      3) type属性： 操作指令
- [preloadedState] state初始值
- [enhancer] 增强器

1. 定义 reducer 
2. 创建仓库 createStore
3. 每次修改过程：  store.dispatch 发送一个修改指令给 reducer，reducer 接收到数据之后，对 state 进行操作，并且返回一个操作后的新的state，然后 触发 监听器，在调用 getState 时，就可以拿到新的 state

### 纯函数
1. 函数的返回结果只依赖于它的参数 (可预测化的状态)
2. 函数执行过程里面没有副作用。
    1) 不依赖外部变量
    2) 不修改外部变量

### 中间件
中间件(applyMiddleware)就是一个函数，对store.dispatch方法进行了改造，在发出 Action 和执行 Reducer 这两步之间，添加了其他功能。
dispatch 发出命令 --> 中间件 -->reducer 做出响应操作
- redux-thunk 
    添加了 redux-thunk 的中间件之后，可以让我们的 dispatch 接收一个函数
    - 如果 dispatch 传入对象，直接通知 reducer 修改，如果传入一个函数，就先执行这个函数

### react-redux
- 安装
yarn add react-redux / npm i react-redux
- 使用
   - `<Provider store>` 使<font color="orange">组件层级中的 connect() 方法</font>都能够获得 Redux store。正常情况下，你的根组件应该嵌套在 `<Provider>` 中才能使用 connect() 方法
   - Provider 参数：
        store (Redux Store): 应用程序中唯一的 Redux store 对象<br>
        children (ReactElement) 组件层级的根组件。
   - connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])
      连接 React 组件与 Redux store。<br>
      连接操作不会改变原来的组件类。<br>
      反而返回一个新的已与 Redux store 连接的组件类。
   - connect参数：
        `[mapStateToProps(state, [ownProps]): stateProps]` (Function): 如果定义该参数，组件将会监听 Redux store 的变化。任何时候，只要 Redux store 发生改变，mapStateToProps 函数就会被调用。该回调函数必须返回一个纯对象，这个对象会与组件的 props 合并。如果你省略了这个参数，你的组件将不会监听 Redux store。如果指定了该回调函数中的第二个参数 ownProps，则该参数的值为传递到组件的 props，而且只要组件接收到新的 props，mapStateToProps 也会被调用（例如，当 props 接收到来自父组件一个小小的改动，那么你所使用的 ownProps 参数，mapStateToProps 都会被重新计算）