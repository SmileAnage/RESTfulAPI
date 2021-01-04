# RESTful API

### 一、理解RESTful API设计规范

* RESTful是目前最流行的API设计规范，它是用于web数据接口的设计
* REST与技术无关，它代表的是一种软件架构风格。REST它是Representational State Transfer的简称，中文的含义是："表征状态转移" 或 "表现层状态转化"
* 它是基于HTTP、URI、XML、JSON等标准和协议，支持轻量级、跨平台、跨语言的架构设计

### 二、REST设计原则

* 每一个URI代表一种资源
* 同一种资源有多种表现形式(xml/json)
* 所有的操作都是无状态的
* 规范统一接口
* 返回一致的数据格式
* 可缓存(客户端可以缓存响应的内容)

注：符合上述REST原则的架构方式被称为RESTful规范

### 三、URL及参数设计规范

#### 1、uri设计规范

* uri末尾不需要出现斜杠(/)

* 在uri中使用斜杠 / 是表达层级关系的

* 在uri中可以使用连接符(-)，来提升可读性

   ```
  eg:	http://xxx.com/xx-yy 比 http://xxx.com/xx_yy 的可读性更好
   ```

* 在uri中不允许出现下划线(_)

* 在uri中尽量使用小写字符

* 在uri中不允许出现文件扩展名

  ```
  eg:	/xxx/api, 不要写成 /xxx/api.php 这样的是不合法的
  ```

* 在uri中使用复数形式

#### 2、HTTP请求规范

```http
http://xxx.com/api/users;		// GET请求方式 获取所有用户信息
http://xxx.com/api/users/1;		// GET请求方式，获取标识为1的用户信息
http://xxx.com/api/users/1;		// DELETE请求方式，删除标识为1的用户信息
http://xxx.com/api/users;		// POST请求方式，添加新的用户
http://xxx.com/api/users/1;		// PUT请求方式，更新标识为1的用户信息

GET:查询		// 从服务器取出资源
POST:新增		// 在服务器上新建一个资源
PUT:更新		// 在服务器上更新资源
DELETE:删除	// 在服务器上删除资源
```

#### 3、参数命名规范

参数推荐采用下划线命名的方式

```http
http://xxx.com/api/login_name					// 获取当前登录的用户名
http://xxx.com/api/login_name&start_time=time	// 获取多个参数
```

#### 4、状态码范围

```
1xx: 信息，请求收到了，继续处理
2xx: 代表成功，行为被成功地接收、理解及采纳
3xx: 重定向
4xx: 客户端错误，请求包含语法错误或请求无法实现
5xx: 服务端错误
```

#### 5、统一返回格式

RESTful规范中的请求应该返回统一的数据格式。对于返回的数据，一般包含如下字段：

* status: http响应的状态码
* message: 包含文本，比如：success(成功), fail(失败)
* data: 当请求成功时，返回数据信息，否则返回null

```json
// 请求成功
{
    "Status": 200,
    "Message": "查询成功",
    "Data": {
        [1, '小牧', 23],
        [2, '小莫', 22]
    }
}

// 请求失败
{
    "Status": 201,
    "Message": "查询失败",
    "Data": null
}
```

