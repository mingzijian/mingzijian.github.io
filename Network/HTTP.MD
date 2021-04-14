HTTP
--------

**Hyper Text Transfer Protocol**（超文本传输协议）。	
是用于从WWW服务器传输超文本到本地浏览器的传送协议。
HTTP是一个应用层协议，由请求和响应构成，是一个标准的客户端服务器(B/S)模型。
HTTP是一个无状态的协议。

 ![HTTP](https://gitee.com/mingzijian/resources/raw/master/picgo/image-20210414102854107.png)

### HTTP请求

#### HTTP请求消息
##### 请求头

##### 请求体

#### HTTP请求方法

### HTTP响应
#### HTTP响应消息
##### 请求头

##### 请求体

#### HTTP响应状态码
消息响应/成功响应/重定向/客户端错误/服务器端错误
##### 消息响应

| 状态码 | 短语                              | 描述 | 版本支持 |
| ------ | --------------------------------- | ---- | -------- |
| 100    | Continue<br/>(继续)               |      |          |
| 101    | Switching Protocol<br/>(切换协议) |      |          |



##### 成功响应

| 状态码 | 短语                                           | 描述 | 版本支持 |
| ------ | ---------------------------------------------- | ---- | -------- |
| 200    | OK<br/>(成功)                                  |      |          |
| 201    | Created<br/>(已创建)                           |      |          |
| 202    | Accepted<br/>(已接受)                          |      |          |
| 203    | Non-Authoritative Information<br/>(信息未授权) |      |          |
| 204    | No Content<br/>(无内容)                        |      |          |
| 205    | Reset Content<br/>(重置内容)                   |      |          |
| 206    | Partial Content<br/>(部分内容)                 |      |          |



##### 重定向

| 状态码 | 短语                                | 描述 | 版本支持 |
| ------ | ----------------------------------- | ---- | -------- |
| 300    |                                     |      |          |
| 301    |                                     |      |          |
| 302    |                                     |      |          |
| 303    |                                     |      |          |
| 304    | Not Modified<br/>(未修改)           |      |          |
| 305    | Use Proxy<br/>(使用代理)            |      |          |
| 306    |                                     |      |          |
| 307    | Temporary Redirect<br/>(临时重定向) |      |          |
| 308    | Temporary Redirect<br/>(临时重定向) |      |          |



##### 客户端错误

| 状态码 | 短语                                        | 描述 | 版本支持 |
| ------ | ------------------------------------------- | ---- | -------- |
| 400    | Bad Request<br/>(错误请求)                  |      |          |
| 401    |                                             |      |          |
| 402    |                                             |      |          |
| 403    | Forbidden<br/>(禁止访问)                    |      |          |
| 404    | Not Found<br/>(未找到)                      |      |          |
| 405    | Method Not Allowed<br/>(不允许使用该方法)   |      |          |
| 406    | Not Acceptable<br/>(无法接受)               |      |          |
| 407    |                                             |      |          |
| 408    |                                             |      |          |
| 409    |                                             |      |          |
| 410    |                                             |      |          |
| 411    |                                             |      |          |
| 412    |                                             |      |          |
| 413    |                                             |      |          |
| 414    |                                             |      |          |
| 415    | Unsupported Media Type<br/>(媒体类型不支持) |      |          |
| 416    |                                             |      |          |
| 417    |                                             |      |          |



##### 服务器端错误

| 状态码 | 短语                                              | 描述 | 版本支持 |
| ------ | ------------------------------------------------- | ---- | -------- |
| 500    | Internal Server Error<br/>(内部服务器错误)        |      |          |
| 501    | Implemented<br/>(未实现)                          |      |          |
| 502    | Bad Gateway<br/>(网关错误)                        |      |          |
| 503    | Service Unavailable<br/>(服务不可用)              |      |          |
| 504    | Gateway Timeout <br/>(网关超时)                   |      |          |
| 505    | HTTP Version Not Supported<br/>(HTTP版本不受支持) |      |          |



### Cookie/Session
#### Cookie

#### Session

### HTTP缓存

#### 浏览器缓存
##### 本地存储

##### 默认缓存

### HTTP代理

 ![proxy-server](https://gitee.com/mingzijian/resources/raw/master/picgo/image-20210414102737811.png)



