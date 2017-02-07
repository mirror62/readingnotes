# 认识Flux架构模式

## 概念 
**Flux** 是 Facebook 2014年 开源的用于构建用户界面的应用程序框架。

**Flux** 是一种架构思想，专门解决软件的结构问题，比MVC更加简单和清晰

业务逻辑不需要关心数据从哪来，只需要定义好传入的接口，数据应该抽象到其他地方。

含有抽象数据而没有业务逻辑的组件，我们称之为**容器型组件**（container component）

没有数据请求逻辑只有业务逻辑的组件，我们称之为**展示型组件**（presentational component）

## MVC

**MVC**是一种架构设计模式，通过关注数据界面分离，来鼓励改进应用程序结构。

* Model
	* 负责保存应用数据，和后端交互同步应用数据，或校验数据
	* Model改变，View做出反应
	* 与业务数据有关，与应用内交互状态无关 
* View
	* Model的可视化表示，表示当前状态的视图
	* 前端View负责构建和维护DOM元素，对应js模板语言
	* 用户可以与View交互，读取编辑Model,在Model中获取或设置属性值 
* Controller
	* 负责View和Model，M的任何改变会应用到V中，V的操作会通过C应用到M中
	* Backbone包含M和V，但并没有真正的C
	* 管理应用中M和V之间逻辑和协调

## MVVM

* **最大变化**：VM（ViewModel）替代了C（Controller） 
* **关键“改进”**：数据绑定（DataBinding），View的数据状态变化可以直接影响VM，反之亦然。

## MVC的问题

项目越大逻辑越复杂，数据流动方式就越越混乱

eq. 一个庞大Model中某个字段变化后，会触发无数个change事件的回调，整个数据流动的方式也变得更加混乱。

> 解决方式：渲染函数如果只有一个，统一放在Controller中。

## Flux

将应用分成四个部分

* View
	* 职责：负责订阅store中的数据，并使用这些数据渲染相应页面 
	* 视图层
	* react
* Action
	* 视图层发出的消息（比如mouseClick） 
* Dispatcher
	* 职责：分发事件 
	* 用来接收Actions，执行回调函数 
* Store
	* 职责：保存数据，同时响应事件并更新数据
	* 用来存放应用的状态，一旦发生变化，就提醒Views更新页面
	* 不能暴露setter，用于强化数据修改的纯洁性
	* 保证了store的数据确定应用唯一的状态

> controller-view： 将view与store进行绑定，并没有传统MVC中controller需要承担的复杂逻辑。
	
**核心思想**：数据和逻辑永远单项流动




