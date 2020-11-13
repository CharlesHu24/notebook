# node连接mysql生成接口

参考文档：https://www.cnblogs.com/yyzhiqiu/p/12659644.html

### 新认识的软件->`postman`接口测试

> Postman一款非常流行的API调试工具。其实，开发人员用的更多。因为测试人员做接口测试会有更多选择，例如Jmeter、soapUI等。不过，对于开发过程中去调试接口，Postman确实足够的简单方便，而且功能强大。

使用方法，请参考文献：https://www.cnblogs.com/fnng/p/9136434.html



### 在整个过程中，所遇到的问题

#### 数据库报错

>**mysql 报错Error: ER_NOT_SUPPORTED_AUTH_MODE: Client does not support authentication protocol requested by server; consider upgrading MySQL client**

起因：mysql8.0加密方式的原因报错。

**解决办法**

```
# 1.进入数据库

# 2.选择mysql这个数据库

# 3.执行以下指令
alter user 'root'@'localhost' identified with mysql_native_password by '123456';

flush privileges;

# 注意：123456是我自己连接数据库的密码哈
```



### 总结：

首先我们要有一个清晰的逻辑，node作为中间人连接数据库，可以直接操作数据，vue和node之间通过接口联系起来，实现对数据的操作。例如修改数据调用“修改接口”，而“修改接口”调用update的sql语句，此时，vue传过来修改的数据，对应上sql语句里的字段名和id，就可以实现数据的修改。

