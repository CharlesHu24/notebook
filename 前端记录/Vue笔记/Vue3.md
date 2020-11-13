# Vue3新特性

## 一. 为什么要使用Composition API？

- Vue2对于复杂逻辑组件，在后期变得无法维护

- Vue2中代码复用方法，如：Mixin，Filters都有缺陷

### 1.1 Options API

逻辑被拆分成：

- components
- props
- data
- computed
- methods
- 生命周期的方法

### 1.2 Vue2逻辑复用方式

- Mixin（命名空间冲突、逻辑不清晰、不易复用）
- scoped slot作用域插槽（配置项多、代码分裂、性能差）
- Vue2对TS支持不充分



### 1.3 逻辑代码对比

![](E:\CharlesHu\notebook\前端记录\Vue笔记\images\vue3\composition API.png)



中文文档：https://v3.cn.vuejs.org/

组合式API：https://composition-api.vuejs.org/api.html

官方文档：https://v3.vuejs.org/



## 二. Composition API

Composition API（组合式API）



### 2.1 使用Composition API

