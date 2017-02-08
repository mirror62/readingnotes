# Redux

优化和扩展flux方案

* reflux
* fluxxor
* Redux

## Redux是什么
核心代码可以理解成一个库，但同时也强调与Flux类似的架构思想

* 本身指Redux的npm包
* 提供若干API让我们使用reducer创建store
* 更新store中的数据或获取store中最新的状态

## Redux三大原则

1. 单一数据源
	* 一个应用永远只有唯一的数据源（model） 
2. 状态是只读的
	* 与flux不同，没有store
	* 定义了一个reducer
	* createStore方法根据reducer生成store
	* 最后利用store.dispatch方法来达到修改状态的目的 
3. 状态修改均由纯函数完成
	* 这是Redux与Flux在表现上的最大不同
	* 通过定义reducer来确定状态的修改
	* 每一个reducer都是纯函数 

## Redux核心

Redux的核心是一个store，这个store由Redux提供的createStore(reducers[,initialState])方法生成
> 要想生成store，必须要传入reducers，同时可传入第二个可选参数初始化状态(initialState)

### reducers

**职责** ：负责相应 action 并修改数据的角色

**本质** ：是一个函数

**函数签名** ：reducer(previousState,action) => newState

### createStore

Redux 中最核心的API

```js
import { createStore } from 'redux';
const store = createStore(reducers);
```

**store**

* getState()
	* 获取store中当前的状态 
* dispatch(action)
	* 分发一个action
	* 并返回这个action
	* 这是唯一能改变store中的数据的方式 
* subscribe(listener)
	* 注册一个监听者
	* 在store发生变化时被调用 
* replaceReducer(nextReducer)
	* 更新当前store里的reducer
	* 一般只会在开发模式中调用该方法

### react-redux

提供一个组件和api，帮助redux和react进行绑定，

* react组件 < Provider />
	* provider 接收一个store 作为 props
	* 整个redux的顶层组件 
* connect() 
	* 提供在整个 react 应用的任意组件中获取 store 中数据的功能

## Redux middleware 

> 它提供了一个分类处理的 action 的机会。在 middleware 中，你可以检阅每一个流动的 action， 挑选出特定类型的 action 进行相应操作， 给你一次改变 action 的机会。















