# Gin框架安装和使用

> 安装

```go
go get -u github.com/gin-gonic/gin
```

一个简单的例子

`````go
package main

import "github.com/gin-gonic/gin"

func main() {
	// 创建一个默认的路由引擎
	r := gin.Default()
	// GET: 请求方式； /hello:请求路径
	// 当客户端以GET方法请求/hello路径时，会执行后面的匿名函数
	r.GET("/hello", func(c *gin.Context) {
		c.JSON(200, gin.H{
			"message": "hello world",
		})
	})
	// 启动HTTP服务， 默认在0.0.0.0:8080启动服务
	r.Run()
}
`````

启动后在浏览器访问**127.0.0.1：8080**端口就可以；



# RESTful API

基本上公司中后端只需要写接口就行，目前主要是RESTful API

rest与技术无关，代表一种软件架构风格， 表示：表征状态转移或表现层状态转移。

简单来说就是，rest的含义就是客户端与Web服务器交互的时候，使用HTTP协议中的4个请求方法代表不同的动作。

- GET用来获取资源
- POST用来新建资源
- PUT用来更新资源
- DELETE用来删除资源

只要API程序遵循了REST风格，那就可以称其为RESTful API。目前在前后端分离的架构中， 前后端基本都是通过RESTful API来进行交互。





# Gin渲染

## HTML渲染



## JSON渲染

![image-20240110150050782](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110150050782.png)

## XML渲染



## YMAL渲染



## protobuf渲染

![image-20240110150134305](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110150134305.png)



# 获取参数

## 获取querystring参数

指的是URL中？后面携带的参数

![image-20240110150412760](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110150412760.png)

## 获取form参数

当前端请求 的数据通过from表单提交时，例如向/user/search发送了一个POST请求

![image-20240110150911687](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110150911687.png)

## 获取json参数

当前端请求的数据通过JSON提交时，例如向/json发送一个POST请求

![image-20240110151209572](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110151209572.png)

## 获取path参数

请求通过URL路径传递。

![image-20240110151437708](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110151437708.png)

**更方便的获取方式：c.ShouldBind()**:注意：字段首字母大写，tag要对应上，要传指针类型





# 文件上传



![image-20240110160145651](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110160145651.png)

效果图

![image-20240110160211361](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110160211361.png)

不过没有实际的处理上传文件的方式

![image-20240110160347271](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110160347271.png)

![image-20240110161009135](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110161009135.png)



# 重定向

## HTTP重定向

![image-20240110170225122](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110170225122.png)

## 路由重定向

就是指把一个请求交给另一个请求来处理

![image-20240110170257759](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110170257759.png)



# Gin路由

## 普通路由

```go
r.GET("/index", func(c *gin.Context)){...}
r.POST("/index", func(c *gin.Context)){...}
```

此外还有一个可以匹配所有请求方法的Any方法

```go
r.Any("/index", func(c *gin.Context)){...}
```

## 路由组

我们可以把拥有共同URL前缀的路由划分为一个路由组。习惯性的用一对大括号包裹同组路由。

![image-20240110174644822](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110174644822.png)

**支持嵌套**

![image-20240110174634347](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110174634347.png)



# Gin中间件

Gin框架可以在处理请求的过程中加入用户自己的钩子（Hook）函数。适合处理一些公共的业务逻辑，比如登录验证、权限效验、数据分页、记录日志、耗时统计等。

## 定义中间件

Gin中的中间件必须是一个`gin.HandlerFunc`类型的。例如

![image-20240110175208731](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110175208731.png)

## 注册中间件

在gin框架中，我们可以给每个路由添加任意数量的中间件

![image-20240110181446543](E:\Code\Baibang.blog\Go\Gin框架\assets\image-20240110181446543.png)

















