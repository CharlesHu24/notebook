## 一. 了解TypeScript

### 1.1 什么是TypeScript

TypeScript是JS的`超集`,为JS添加了`类型系统`

JS有的TS都有





## 二. 安装和配置TS环境

安装`typescript`包: 将TS 转化为 JS

- 安装: `npm i -g typescript`





## 三.第一个TS文件

### 3.1 创建并执行TS文件

1. 创建TS文件

2. 写代码

3. 执行代码: 分两步

   1. TS代码 -> JS代码: 在当前目录终端中输入 `tsc 文件名.ts`
   2. 执行JS: 输入 `node 文件名.js`

   >`tsc 文件名.ts`会生成一个js文件
   >
   >`node 文件名.js`表示执行JS文件中的代码

### 3.2 简化执行TS的步骤

安装`ts-node`包，"直接"在Node.js中执行TS代码

- 安装: `npm i -g ts-node`
- 使用: `ts-node 文件名.ts`

>ts-node包内部偷偷地将TS -> JS, 之后执行JS代码



## 四. TS变量的类型

### 4.1 变量类型的体现

```ts
let age: number = 18;
```



### 4.2 变量命名规则

- 变量名只能出现: 数字、字母、下划线、美元符号，并且不能以数字开头

- 变量名区分大小写



### 4.2 基本数据类型

| 数据类型  | 备注       |
| --------- | ---------- |
| number    | 数字类型   |
| string    | 字符串类型 |
| boolean   | 布尔类型   |
| undefined | 未定义     |
| null      | 空         |

后续还有对象类型(复杂的数据类型)



### 4.2 undefined和null

- `undefined`: 定义了 但是没有值
- `null`: 有值 值就是null



## 五.数组类型

### 5.1 创建数组

- 语法一（推荐）：

  ```ts
  let names: string[] = ['阿衰', '大脸妹', '老夫子']
  ```

  数组的类型注解由两部分组成：`类型+[]`。

- 语法二（不推荐）：

  ```ts
  let names: string[] = new Array('阿衰', '大脸妹', '老夫子')
  
  // 相当于
  
  let names: string[] = ['阿衰', '大脸妹', '老夫子']
  ```

  

## 六. 函数

~~~ts
function fn(str: string) {
	...
}
~~~

### 6.1 函数参数

形参和实参的总结：

- 声明函数时的参数，叫什么？作用？ -> 形参，指定函数能够接收什么数据
- 调用函数时的参数，叫什么？作用？ -> 实参，是一个具体的值，用来赋值给形参

### 6.2  函数返回值

#### 6.2.1 概述

`函数返回值`的作用：`将函数内部计算的结果返回`，以便于使用该结果继续参与其他的计算

关键点：`拿到函数内部计算出来的结果`，然后，才能进行后续的计算

注意：如果没有指定函数的返回值，那么，`函数返回值的默认类型为void`（空，什么都没有）

#### 6.2.2 基本使用

1. 指定返回值类型

   ```ts
   function fn(): number {
   	...
   }
   ```

2. 指定返回值

   ```ts
   function fn(): number {
   	return 返回值
   }
   ```

- 注意：`返回值必须符合返回值类型的类型要求，否则会报错`

### 6.3. 函数调试

#### 6.3.1 基本操作

![](E:\CharlesHu\notebook\前端记录\TypeScript笔记\images\调试函数.png)

## 七. 对象

### 7.1 概述

对象：`一组相关属性和方法的集合，并且是无序的`

### 7.2 函数和方法的区别

> 如果一个函数是单独出现的，没有与对象关联，我们称为函数；否则，称为方法

### 7.3 对象的类型注解

> `对象是结构化`的，在使用对象前，就根据需求，提前设计好对象的结构
>
> 对象的结构化类型（类型注解）：`建立一种契约，约束对象的结构`

```ts
// 类型注解（设计对象的结构）
let person: {
  name: string;
  age: number;
}

// 为对象中的属性赋值
person = {
  name: 'hcl',
  age: 18
}
```

### 7.4. 接口

- 直接在对象名称后面写类型注解的坏处：1 代码结构不简洁 2 无法复用类型注解

- 接口：为对象的类型注解命名，并为你的代码建立契约来约束对象的结构

- 语法：

  ```ts
  // 创建一个接口
  interface IUser {
    name: string;
    age: number
  }
  
  // 使用接口
  let p1: IUser = {
    name: 'hcl',
    age: 18
  }
  
  let p2: IUser = {
    name: 'zz',
    age: 24
  }
  ```

  `interface`表示接口，结构名称约定以`I`开头



### 7.5 内置对象

#### # forEach

```ts
arr.forEach((item, index) => {
  console.log('索引', index, '元素', item)
})
```



forEach方法的执行过程：遍历整个数组，为数组的每一项元素，调用一次回调函数

注意：forEach方法的参数是一个函数，这也叫**回调函数**

#### # some

some方法：遍历数组，查找是否有一个满足条件的元素（如果有，就可以停止循环）

```ts
let has: boolean = arr.some((num) => {
  if (num > 10) 
    return true
  return false
})
```

some方法返回值：布尔值

### 7.6 类型推论

某些没有明确指出类型的地方，类型推论会帮助提供类型

发生类型推论的2种常见场景：1 声明变量并初始化时，2 决定函数返回值时

```ts
let age: number = 18 // let age = 18

function sum(n1: number, n2: number): number{
	return n1 + n2
}
// ->
function sum(n1: number, n2: number) {
	return n1 + n2
}
```

## 八. 浏览器

### 8.1 浏览器中运行TS

浏览器无法直接运行TS，因此将TS转化为JS然后再运行

```
tsc --watch index.ts
```

解释：--watch表示启用见识模式，只要重新保存了ts文件，就会自动调用 tsc 将 ts 转化为 js 

### 8.2 类型断言

手动指定`更加具体`的类型（比如，元素都是Element类型，更加具体）

语法：

> 值  as  更具体的类型

比如：

```ts
let img = document.querySelector('#image') as HTMLImageElement
```

解释：我们确定id="image"的元素是图片元素，所以，类型指定为HTMLImageElement

技巧：通过`console.dir()`答应DOM元素，在属性的最后面即可看到该元素的类型

- 使用场景：当你比TS更了解某个值的类型，并且需要指定更具体的类型时。

### 8.3 样式操作

1. `dom.style.样式`：单个样式

2. 类样式（classList）的操作有三种

   ```ts
   // 添加
   dom.classList.add(’样式名‘, '样式名')
   // 移除
   dom.classList.remove(’样式名‘, '样式名')
   // 判断是否存在
   let has = dom.classList.contains(样式名)
   ```

   

### 8.4 事件

只需要触发一次，可以在添加事件时，通过`once`属性实现