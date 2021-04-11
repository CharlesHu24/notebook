## 使用element遇到的一些小问题

### 一. `el-image`组件

在使用`el-image`组件时，对路径的处理

```
<el-image :src="require('@/assets/img/ming.jpg')" :fit="fill"/>

--------------or----------------

<el-image :src="headImg" :fit="fill"/>

data () {
  return {
   headImg: require('@/assets/img/ming.jpg')
  }
}
```



