### 第一课

#### MongoDB 分布式数据库

- json对象存储

- MongoDB 是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。





- 物理数据库 -> 数据以什么方式存放
- 概念数据库 -> 逻辑上的
- 用户数据库 -> 用户看到的



#### 关系型和非关系型数据库

关系型(Oracle、SQLServe、mySQL): 目前最主流的数据库、需先设计数据结构

非关系型(NoSQL): 不需要设计数据结构、动态存储数据



#### NoSQL数据库

Not Only SQL -> 非关系型的数据库(分布式存储)



#### NoSQL分类

- 键/值存储数据库
- 列存储数据库
  - 针对海量数据
- 文档型数据库
- 图型数据库



#### NoSQL特征

---



### 第二课

#### MongoDB命令

- `show dbs` -> 查看数据库
- `db`  -> 当前连接的数据库
- `use` -> 切换数据库
- `show collections` or `show tables` -> 查看集合
- `db.collection.find()` -> 查询文档(以行形式)
- `db.collection.find().pretty()` -> 查询文档(对文档进行格式化)

#### 关系型 和 非关系型的对应术语

| 关系   | 非关系                          |
| ------ | ------------------------------- |
| 数据库 | 数据库                          |
| 表格   | 集合                            |
| 行     | 文档                            |
| 列     | 字段                            |
| 表联合 | 嵌入文档                        |
| 主键   | 主键(MongoDB 提供了 key 为 _id) |

#### 元数据

```
# 系统集合
dbname.system.*	 
```



#### MongoDB数据类型

| 数据类型     | 描述                                                         |
| ------------ | ------------------------------------------------------------ |
| Integer      | 整型数值。用于存储数值。根据你所采用的服务器，可分为 32 位或 64 位。 |
|              |                                                              |
|              |                                                              |
| Min/Max keys | 将一个值与 BSON（二进制的 JSON）元素的最低值和最高值相对比。 |
|              |                                                              |
|              |                                                              |
|              |                                                              |



#### 获取文档创建时间戳

```
# 查看时间戳
# 格林尼治时间，非北京时间
> var newObject = ObjectId()
> newObject.getTimestamp()

# ObjectId转换为字符串
> newObject.str
```

### 第三课

#### 创建用户

现版本和老版本有所区别，老版本的不再使用现在的版本

```json
db.createUser({user: "testUser", pwd: "123456", roles: [{role: "userAdminAnyDatabase", db: "admin"}]})
```

### 第四课

#### 列出用户

```
# 第一种
show users

# 第二种
# 这种方式会返回一个游标对象，可用它来访问user文档
use admin
cur = db.system.users.find()
cur.count()
```



#### 删除用户

```
# 先切换到用户所在数据库
use db_name
db.dropUser("user_name")
```



#### Connection对象

- Connection对象的方法

  | 方法                 | 描述                                  |
  | -------------------- | ------------------------------------- |
  | new Mongo(host:port) | 连接MongoDB，并返回Connection对象实例 |
  | getDB(database)      | 返回一个db对象（指定的数据库）        |
  | ...                  |                                       |



#### 切换其他数据库

```
use db_name

db = db.getSiblingDB('db_name')
```



#### 创建数据库

```
use db_name

# 添加集合
db.createCollection("collection_name")
```



#### 删除数据库

```
# 删除当前数据库
use db_name
db.dropDatabase()
```



#### JS中创建数据库

```js
// 创建一个connection实例
var myConn = new Mongo("localhost")

// 使用connection实例中的getDB方法创建Database对象
var myDB = myConn.getDB("myDB")

// 在这个Database对象中创建添加集合
myDB.createCollection("newCollection")
```



### 第五课

#### 查看集合

```
show collections

# 以数组格式显示，使用方法
db.getCollectionNames()
```



#### 创建集合

```
use test
db.createCollection("newCollection")
```



#### 删除集合

```
# 方法一
use test
db.newCollection.drop()

# 方法二
coll = db.getCollection("newCollection")
coll.drop()

```



### 原始代码问题

```
# 去除如下语句
console.log(e)
console.log(err)

db.word_stats.remove();
```



