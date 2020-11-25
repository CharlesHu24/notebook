## Blog项目记录



### 把blog页面抽离成合适的组件

#### 组件中的数据

- 静态数据

- 动态数据（前端的方法做）

  - 数据封装

  ```
  export class Blog {
    constructor(itemInfo) {
    	this.img = itemInfo.img
      this.title = itemInfo.title	// String
      this.author = itemInfo.author	// string
      this.describe = itemInfo.describe // string
      this.tag = itemInfo.tag
      this.heart = itemInfo.heart
      this.commentsColumn = itemInfo.commentsColumn
    }
  }
  ```



#### 抽离blog组件有两种做法

- 第一种

  在`BlogList`组件预留一个插槽，`BlogListItem`组件中给每一项数据预留一个具名插槽；将这两个组件统一交给`MainBlog`组件管理，通过具名插槽控制数据

  ```vue
  // MainBlog.vue
  <BlogList>
    <BlogListItem>
      <img slot="blogItem-img" src="../../../../public/images/blog/timeline/1.jpg" class="img-responsive" alt="">
      <span slot="blogItem-title">用炸弹放火烧山</span>
      <span slot="blogItem-author">ss军</span>
      <span slot="blogItem-desc">原神里面ss用可莉打丘丘人，放火烧山</span>
      <span slot="blogItem-tag">
        <span>life</span>
        <span>green</span>
      </span>
      <span slot="blogItem-heart">999</span>
      <span slot="blogItem-comments-col">8</span>
    </BlogListItem>
  </BlogList>
  ```

  **这种方式有一个弊端，有多少条博客数据就要手动添加多少个组件**

- 第二种方式

  不使用插槽的方式，将`BlogListItem`组件放入`blogList`中，对`blogListItem`组件进行循环，动态获取数据，有多少条博客，就循环多少个组件

  循环整个数据，将每条数据传到`BlogListItem`里面

  ```vue
  // BlogList.vue
  <template>
    <div class="col-md-9 col-sm-7">
      <div class="row">
        <BlogListItem v-for="item in blog" :blog-item="item"></BlogListItem>
      </div>
      ...
    </div>
  </template>
  ```

  

  `BlogListItem`拿到每条博客相应的数据

  ```vue
  // BlogListItem.vue
  <template>
    <div class="col-md-6 col-sm-12 blog-padding-right">
      <div class="single-blog two-column">
        <div class="post-thumb pointer">
          <a @click="itemClick">
            <!--        blogItem.img-->
            <img :src="blogItem.img" class="img-responsive" alt="">
          </a>
          <div class="post-overlay">
            <!--        blogItem.date-->
            // 暂时没弄
            <!--  -------------------分割线---------------------  -->
            <!--  2019.11.9使用split方法分割，然后放进来  -->
            <span class="uppercase"><a>14 <br><small>Feb</small><small>2013</small></a></span>
          </div>
        </div>
        <div class="post-content overflow">
          <!--      blogItem.title-->
          <h2 class="post-title bold pointer" @click="itemClick"><a>{{blogItem.title}}</a></h2>
          <!--      blogItem.author-->
          <h3 class="post-author"><a>{{blogItem.author}}</a></h3>
          <!--      blogItem.describe-->
          <!--      截取文章开头X个字-->
          <p>{{blogItem.describe}}[...]</p>
          <!--      查看详情-->
          <span class="pointer">
            <a class="read-more" @click="itemClick">View More</a>
          </span>
          <div class="post-bottom overflow">
            <ul class="nav nav-justified post-nav pointer">
              <!--          blogItem.tag-->
              <li class="blogItem-tag">
                <span>
                  <a><i class="fa fa-tag"></i></a>
                  <a v-for="item in blogItem.tag">{{item}}</a>
    						</span>
              </li>
              <!--          blogItem.heart-->
              <li><a><i class="fa fa-heart"></i>{{blogItem.heart}} Love</a></li>
              <!--          blogItem.commentsColumn-->
              <li><a><i class="fa fa-comments"></i>{{blogItem.commentsColumn}} Comments</a></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
</template>
  ```

  **这样动态控制组件的个数**
  
  







#### vue-router配置

#### blog-detail页面  根据id获取对应的数据

- 动态数据



### blog页面和detail页面部分相似的组件



`header`

`footer`

`breadcrumb`

`content-main`

`content-sidebar`

`content-main`中具体放什么根据内容决定，`content-main`提供布局

