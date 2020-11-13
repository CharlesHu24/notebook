## 一. 响应式开发

### 1.1 响应式开发原理

- 一种布局适配多个设备

- 针对不同宽度的设备进行布局和样式的设置

| 设备                   | 尺寸区间         |
| ---------------------- | ---------------- |
| 超小屏幕(新增规格)     | < 576px          |
| 小屏幕(次小屏)         | >= 576px ~ 768px |
| 中等屏幕(平板)         | >= 768px ~ 992px |
| 大屏幕(桌面显示器)     | >=992px ~ 1200px |
| 超大屏幕(大桌面显示器) | >= 1200px        |

### 1.2 响应式布局容器

响应式需要一个父级作为布局容器，来配合子级元素来实现变化效果

#### 平时我们的响应式尺寸划分

- 超小屏幕(新增规格，小于576px)：设置宽度100%

- 小屏幕(次小屏，大于等于576px  ) ：设置宽度540px
- 中等屏幕(平板，大于等于768px  ) ：设置宽度720px
- 大屏幕(桌面显示器，大于等于992px ) ：设置宽度960px
- 超大屏(大桌面显示器，大于等于1200px )：设置宽度1140px

```
# 媒体查询
@media
```

## 二. Bootstrap初体验

### 2.1 基本模板

```html
<!DOCTYPE html>
<html lang="zh-cn">
<head>
  <meta charset="UTF-8">
  <!--  做设备适应-->
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <!--  引用css-->
  <link rel="stylesheet" href="css/bootstrap.css">
  <title>Title</title>
</head>
<body>

<!--引用js-->
<script src="js/bootstrap.js"></script>
</body>
</html>
```

- 构建bootstrap所需配置

```html
<!--  做设备适应-->
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  
<!--  引用bootstrap的css-->
<link rel="stylesheet" href="css/bootstrap.css">
  
<!--引用bootstrap的js-->
<script src="js/bootstrap.js"></script>
```



### 2.2 注意事项

- 响应式`meta`标签：响应式meta标签：为了确保所有的设备的渲染和触摸效果，必须在`<head></head>`区域添加响应式的视图标签
- 盒尺寸：Bootstrap将全局的`box-sizing`的值由默认的`content-box`重定义为`border-box`；若要恢复尺寸如下代码

```css
.selector-for-some-widget {
	box-sizing: content-box;
}
```

## 三. 布局

### 3.1 容器

Container容器是窗口布局的最基本元素，推荐所有样式都定义在`.container`或`.container-fluid`容器之中-- **这是启用整个栅格系统必不可少的前置条件**

- 默认响应式容器

```html
<div class="container">
  <!-- 网页内容写在这里面 -->
</div>
```

- 流式布局

```html
<div class="container-fluid">
  ...
</div>
```

### 3.2 栅格系统

基于12列布局，12为基数。使用`.container`容器作为父盒子，内部由行(.row)和列(.col)组成，

**所呈现的内容必须放在列(.col-*)中**，而且只有列可以是行的直接子元素，否则都是违法的

- 简单来说：有一个容器，容器里面有行，行里面有列，一共可以放12列

#### 3.2.1 栅格选项

|                       | 超小屏幕 (新增规格)<576px | 小屏幕 次小屏≥576px | 中等屏幕 窄屏≥768px | 大屏幕 桌面显示器≥992px | 超大屏幕 大桌面显示器≥1200px |
| --------------------- | ------------------------- | ------------------- | ------------------- | ----------------------- | ---------------------------- |
| `.container` 最大宽度 | None (auto)               | 540px               | 720px               | 960px                   | 1140px                       |
| 类前缀                | `.col-`                   | `.col-sm-`          | `.col-md-`          | `.col-lg-`              | `.col-xl-`                   |
| 列（column）数        | 12                        |                     |                     |                         |                              |
| 列间隙                | 30px (每列两侧各15px)     |                     |                     |                         |                              |
| 可嵌套性              | Yes                       |                     |                     |                         |                              |
| 可排序性              | Yes                       |                     |                     |                         |                              |

- 屏幕的大小是真正的“断点”，即如果只定义一个屏幕规格即可向上覆盖所有设备，向下如果没有定义则默认为12栅格占位

#### 3.2.2 对齐方式

- 对容器：
  - 垂直对齐：`align-items-`
  - 水平对齐：`justify-content-`
- 对元素：
  - 垂直：`align-self-`
  - 水平：``

**跟flex布局用法相同**

#### 3.2.3 间隙沟槽(gutters)

默认列是有间隙的(15px)，如果不想要可以清除间隙`no-gutters`

```css
.no-gutters {
	margin-right: 0;
	martgin-left: 0;
}

.no-gutters > .col,
.no-gutters > [class*="col-"] {
	padding-right: 0;
	padding-left: 0;
}
```



#### 3.2.4 Class顺序重定义

使用`.order-*`class选择器，通过定义`*`的数字，手动设置列的排序，没设置排序的，按默认位置。



#### 3.2.5 列偏移

使用`.offset-*`class选择器，通过定义`*`的数字，实现列偏移

- 当没有达到12列时，设置偏移，从左边开始计算偏移多少个列

---

## 图片

- Picture元素

```html
<picture>
  <source srcset="大规格图片.jpg"  media="(min-width: 800px)" >
  <source srcset="中规格图片.jpg"  media="(min-width: 600px)">
  <source srcset="小规格图片.jpg">
  <img src="通用图片.jpg" alt="这是当浏览器不支持picture标签时显示的图片">
</picture>
```

