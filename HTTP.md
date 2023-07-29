[深入理解HTTP协议](https://zhuanlan.zhihu.com/p/45173862)

# http概述

超文本传输协议HyperText Transfer Protocol，一种基于TCP协议的应用层传输协议，简单来说就是客户端和服务端进行数据传输的一种规则。

`HTTP` 是一种**无状态** (stateless) 协议， `HTTP` 协议本身不会对发送过的请求和相应的通信状态进行**持久化处理**。这样做的目的是为了保持HTTP协议的简单性，从而能够快速处理大量的事务, 提高效率。

然而在许多场景中，我们需要保持用户登陆状态或者记录购物车中的商品。由于 `HTTP` 协议是**无状态协议**，我们需要一些技术来管理状态，即 `COOKIE`

> 什么是非持久化处理？
> 可以简单理解为每次请求都需要重新建立TCP链接
> 相对的有持久化处理，这一系列的请求相应都通过第一次的TCP链接进行

# 请求

![[Pasted image 20230728162604.png]]

## 请求行 general

包括**请求方法**，**请求链接**，以及**HTTP协议的版本**

这里详细说明一下请求方法

### 请求方法

根据HTTP标准，HTTP请求可以使用多种请求方法。  
HTTP的1.0版本中只有三种请求方法： `GET`, `POST` 和 `HEAD`方法。到了1.1版本时，新增加了五种请求方法：`OPTIONS`, `PUT`, `DELETE`, `TRACE` 和 `CONNECT` 方法。

[(50条消息) http请求方法（GET、POST、HEAD、OPTIONS、PUT、DELETE、TRACE、CONNECT）_番薯大佬的博客-CSDN博客](https://blog.csdn.net/potato512/article/details/76696582)

## 请求报头 header 

由一系列键值对构成，用于发送一些附加信息，主要包括如下

![[Pasted image 20230728164341.png]]

## 请求正文 body

`POST` 方法有正文，而 `GET` 方法没有

# 响应

![[Pasted image 20230728162755.png]]

## 状态行 general

包括**版本信息**，**状态码**，以及**对状态码的文本描述**

### 状态码

状态代码有三位数字组成，第一个数字定义了响应的**类别**，且有五种可能取值： _`1xx`：**指示信息** - 表示请求已接收，继续处理_ `2xx`：**成功** - 表示请求已被成功接收、理解、接受 _`3xx`：**重定向** - 要完成请求必须进行更进一步的操作_ `4xx`：**客户端错误** - 请求有语法错误或请求无法实现 * `5xx`：**服务器端错误** - 服务器未能实现合法的请求

![[Pasted image 20230728164616.png]]
![[Pasted image 20230728164626.png]]
![[Pasted image 20230728164647.png]]

## 消息报头 header

同样的键值对

## 正文 response

传输的数据