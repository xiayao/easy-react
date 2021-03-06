# 框架(第一稿)文档
##  前言
#### 本框架主要解决ReactJS View层事件逻辑过多和多层组件之间父-子数据传递的嵌套问题
## 主要作用
#### 1.通过创建数据管理器DataComm的单例,管理全局storage,实现基于ReactJS框架下任意组件之间的数据传递;
#### 2.抽出具体的处理逻辑到Action中，避免在组件中直接处理太多的事件逻辑
## 使用方法
#### 1.引入自定义的basecomp.js,创建继承自BaseComp的的自定义组件,让它拥有BaseComp基类中定义的方法;
#### 2.编写自定义Action,并调用DataComm单例注册该Action;
#### 3.在自定义组件中调用exec(),调用指定的Action;
#### 4.在自定义组件中通过bindData(),将获取到的数据绑定到组件的state中
## 主要组件方法
#### 1.事件执行方法
##### /*
##### * 本方法实现对指定Action的调用,并传递参数给Action中的对应方法进行处理
##### * Action.actionType: 第一个参数,必选,包括指定的方法集名称(Action)和方法名称(actionType),以"."分隔
##### * arg1, arg2, ...: 传递给指定方法的参数,可选
##### */
##### this.exec(Action.actionType, arg1, arg2,....) {
##### ... ...
##### }
#### 2.数据绑定方法
#####/*
##### * 实现全局storage中的指定数据和组件state中指定数据的绑定
##### * property      : 要获取的数据的名称
##### * stateProperty : 组件state中要绑定的数据的名称
#####*/
##### this.bindData(property, stateProperty) {
##### ... ...
#####}
## 示例代码
#### 代码位置: examples/index.html
#### 代码特点:
##### 1)实现绑定输入框初始值到显示区域;
##### 2)点击"确认"按钮，同步输入结果到显示区域
