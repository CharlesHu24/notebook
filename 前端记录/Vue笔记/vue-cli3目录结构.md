## 简单介绍vue

### 一. vue-cli4目录结构



|-- dist  --->  运行`npm install build`后，打包生成的文件夹，用于生产环境
|-- node_modules  --->  安装的依赖包
|-- public  --->  public中的静态资源会被复制到输出目录(dist)中
|    |-- index.html  --->  入口页面
|-- src  --->  项目核心文件夹，写代码的地方
|    |-- assets  --->  放置一些静态资源，会被打包压缩
|    |-- components  --->  一些公共组件
|    |-- router  --->  vue-router相关配置
|    |-- store  --->  vuex相关配置，存放公共变量
|    |-- views  --->  页面编写的地方（页面使用组件拼出来的，也是vue文件）
|    |-- App.vue  --->  vue页面的根组件
|    |-- main.js  --->  vue入口文件
|-- .browserslistrc  --->  用来对浏览器进行限制的
|-- .gitignore  --->  git上传需要忽略的文件格式
|-- babel.config.js  --->  babel语法转化，ES6转化成ES5
|-- package.json  --->  项目基本信息（项目开发所需的模块，项目名称、版本）
|-- readme.md  --->  说明项目（如何使用，注意事项等等）
|-- vue.config.js  --->  可选文件（对vue-cli以及webpack可以进行一些配置）



### 二. 初始化vue项目（创建vue项目）

```
# 创建一个名为vue-test的项目
vue create vue-test
```

#### 1. 自定义配置项目

![](E:\CharlesHu\notebook\前端记录\Vue笔记\images\vue-cli4\01.vue-create.png)



#### 2. 选择所需配置项

![](E:\CharlesHu\notebook\前端记录\Vue笔记\images\vue-cli4\02.manually-select.png)



#### 3. 选择vue版本

![](E:\CharlesHu\notebook\前端记录\Vue笔记\images\vue-cli4\03.vue-version.png)



#### 4. 路由模式选择

![](E:\CharlesHu\notebook\前端记录\Vue笔记\images\vue-cli4\04.router-mode.png)



#### 5. 配置文件管理

![](E:\CharlesHu\notebook\前端记录\Vue笔记\images\vue-cli4\05.select-package.png)



#### 6. 保存当前预设

![](E:\CharlesHu\notebook\前端记录\Vue笔记\images\vue-cli4\06.save-preset.png)



#### 搞定，项目初始化完成