## 一.Sass介绍

sass是预编译语言  sass是css的扩展语言

## 二.安装Sass

```
npm install -g sass
```

## 三. .sass和.scss文件的区别

- sass文件

没有大括号

```
$font-stack:    Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color

```



- scss文件

有大括号 更符合css样式规范，`我更多用这一种`

```
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

## 四. scss文件两种输出方式

- 对单个文件

```
sass --watch input.scss output.css
```

`--watch` 实时监听源文件更改

- 对目录

使用文件夹路径作为输入和输出，并用冒号分隔它们

```
sass --watch app/sass:public/stylensheets
```

## 五.Sass讲解

- 变量：sass使用`$`定义变量

- `&`的使用：父选择器的标识符,代替父元素

```
input.scss

a {
  color: blue;
  &:hover { color: red }
}
```

```
output.css

a { color: blue; }
a:hover { color: red; }
```



- 引用Sass文件：

```
_part.scss

$primary-color:red;
```

```
input.scss

@import "part" // 引用scss文件(可去掉后缀和下划线 _)
body {
	background-color: $primary-color; // 并使用其中的变量
}
```

- `@mixin`和`@include`：

  - `@mixin`: **定义** css声明组(一组css样式)

  ```
  @mixin xuanzhuan($property) { 
    transform: $property;
  }
  ```

  - `@include`:**引用**css声明组(里面可以传参数)

  ```
  .box1 { @include xuanzhuan(rotate(30deg)); }
  .box2 { @include xuanzhuan(rotate(70deg)); }
  ```

- `@extend`和`%`的使用

  - `%`:**定义**可复用(公用的)的css样式组

  ```
  %message-shared {
  	color: red;
  	border: 1px solid yellow;
  }
  ```

  - `@extend`:继承; 使用`%`定义的样式组都可以用`@extend`继承

  ```
  .message {
    @extend %message-shared; //继承了该css样式组
  }
  
  .success {
    @extend %message-shared;
    border-color: green; //额外定义的
  }
  ```

- 运算符

```
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="right"] {
  float: right;
  width: 300px / 960px * 100%;
}
```

